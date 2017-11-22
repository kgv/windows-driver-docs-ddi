---
UID: NF.wdm.KeSetSystemGroupAffinityThread
title: KeSetSystemGroupAffinityThread
author: windows-driver-content
description: The KeSetSystemGroupAffinityThread routine changes the group number and affinity mask of the calling thread.
old-location: kernel\kesetsystemgroupaffinitythread.htm
ms.assetid: 8ccc097d-f997-43c1-a068-f2f532afa0d6
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Wdm.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 7.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KeSetSystemGroupAffinityThread
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL (see Remarks section).
ms.keywords: KeSetSystemGroupAffinityThread
req.iface: 
req.product: Windows 10 or later.
---

# KeSetSystemGroupAffinityThread function



## -description
<p>The <b>KeSetSystemGroupAffinityThread</b> routine changes the group number and affinity mask of the calling thread.</p>


## -syntax

````
VOID KeSetSystemGroupAffinityThread(
  _In_      PGROUP_AFFINITY Affinity,
  _Out_opt_ PGROUP_AFFINITY PreviousAffinity
);
````


## -parameters
<dl>

### -param <i>Affinity</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546539">GROUP_AFFINITY</a> structure that specifies the new group number and group-relative affinity mask for the calling thread.</p>
</dd>

### -param <i>PreviousAffinity</i> [out, optional]

<dd>
<p>A pointer to a caller-allocated <b>GROUP_AFFINITY</b> structure into which the routine writes information about the previous group affinity of the calling thread. The caller can later use this pointer as an input parameter to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553195">KeRevertToUserGroupAffinityThread</a> routine to restore the previous thread affinity. Frequently, <b>KeSetSystemGroupAffinityThread</b> writes values to this structure that are not valid group affinities but that have special meaning to <b>KeRevertToUserGroupAffinityThread</b>. Do not supply pointers to these special values as <i>Affinity</i> parameters in subsequent <b>KeSetSystemGroupAffinityThread</b> calls.</p>
<p>If necessary, the caller can change the thread affinity more than once by calling <b>KeSetSystemGroupAffinityThread</b> multiple times. During the first of these calls, the caller should specify a non-<b>NULL</b> value for <i>PreviousAffinity</i> so that the original thread affinity can be captured and later restored. However, the later calls to <b>KeSetSystemGroupAffinityThread</b> can, as an option, set <i>PreviousAffinity</i> = <b>NULL</b>. For more information, see Remarks.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>This routine changes the group number and group-relative affinity mask of the calling thread. The <i>Affinity</i> parameter points to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546539">GROUP_AFFINITY</a> structure. The group number and affinity mask in this structure identify a set of processors on which the thread can run. If successful, the routine schedules the thread to run on a processor in this set.</p>

<p>If the <i>PreviousAffinity</i> parameter is non-<b>NULL</b>, the routine saves information about the previous group affinity, which were in effect at the start of the call, in the <b>GROUP_AFFINITY</b> structure that <i>PreviousAffinity</i> points to. To restore the previous thread affinity, the caller can supply the pointer to this structure as an input parameter to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553195">KeRevertToUserGroupAffinityThread</a> routine.</p>

<p>In a multiprocessor system, a kernel-mode driver routine that runs in the context of a user-mode thread might need to call <b>KeSetSystemGroupAffinityThread</b> to temporarily change the group affinity of the thread. Before the routine exits, it should call <b>KeRevertToUserGroupAffinityThread</b> to restore the affinity mask of the thread to its original value.</p>

<p>A process can have affinity for more than one group at a time. However, a thread can be assigned to only one group at any time. That group is always in the affinity of the thread's process. A thread can change the group to which it is assigned by calling <b>KeSetSystemGroupAffinityThread</b>.</p>

<p><b>KeSetSystemGroupAffinityThread</b> changes the group number and affinity mask to the values that are specified in *<i>Affinity</i> only if the following are true:</p>

<p>The group number is valid.</p>

<p>The affinity mask is valid (that is, only mask bits that correspond to logical processors in the group are set).</p>

<p>At least one of the processors that is specified in the affinity mask is active. </p>

<p>If any of these conditions is not met, the group number and affinity mask of the thread remain unchanged. If <i>PreviousAffinity</i> is non-<b>NULL</b>, the routine writes zero to both the group number and the affinity mask in *<i>PreviousAffinity</i>.</p>

<p>Additionally, <b>KeSetSystemGroupAffinityThread</b> writes zero to both the group number and the affinity mask in *<i>PreviousAffinity</i> if the previous group affinity was assigned to the thread in user mode. In response to a <b>GROUP_AFFINITY</b> structure in which the group number and affinity mask are both zero, <b>KeRevertToUserGroupAffinityThread</b> restores the current user-mode thread affinity. If the user-mode thread affinity changes between the <b>KeSetSystemGroupAffinityThread</b> and <b>KeRevertToUserGroupAffinityThread</b> calls, the most recent user-mode affinity is assigned to the thread. (An application can call a function such as <a href="base.setthreadgroupaffinity">SetThreadGroupAffinity</a> to change the user-mode group affinity of a thread.)</p>

<p>Before the new affinity mask in *<i>Affinity</i> takes effect, <b>KeSetSystemGroupAffinityThread</b> removes (sets to zero) any affinity mask bits that correspond to processors that are not currently active. In a subsequent <b>KeSetSystemGroupAffinityThread</b> call, the value that the routine writes to *<i>PreviousAffinity</i> might contain an affinity mask that has been modified in this way.</p>

<p>A related routine, <a href="https://msdn.microsoft.com/library/windows/hardware/ff553271">KeSetSystemAffinityThreadEx</a>, changes the affinity mask of the calling thread, but this routine, unlike <b>KeSetSystemGroupAffinityThread</b>, does not accept a group number as an input parameter. Starting with Windows 7, <b>KeSetSystemAffinityThreadEx</b> assumes that the affinity mask refers to processors in group 0, which is compatible with the behavior of this routine in earlier versions of Windows that do not support groups. This behavior ensures that existing drivers that call <b>KeSetSystemAffinityThreadEx</b> and that use no group-oriented features will run correctly in multiprocessor systems that have two or more groups. However, drivers that use any group-oriented features in Windows 7 and later versions of the Windows operating system should call <b>KeSetSystemGroupAffinityThread</b> instead of <b>KeSetSystemAffinityThreadEx</b>.</p>

<p><b>KeSetSystemGroupAffinityThread</b> and <b>KeRevertToUserGroupAffinityThread</b> support a variety of calling patterns. Two examples are shown in the following diagrams.</p>

<p>The following diagram represents a driver thread that calls <b>KeSetSystemGroupAffinityThread</b> three times to change the thread affinity, and then calls <b>KeRevertToUserGroupAffinityThread</b> to restore the original thread affinity.</p>

<p>In the preceding diagram, the three boxes labeled "Set affinity" are calls to <b>KeSetSystemGroupAffinityThread</b>, and the box labeled "Revert affinity" is a call to <b>KeRevertToUserGroupAffinityThread</b>. The first <b>KeSetSystemGroupAffinityThread</b> call uses the <i>PreviousAffinity</i> output pointer to save the original thread affinity. In the next two calls to <b>KeSetSystemGroupAffinityThread</b> (marked with asterisks), the caller sets <i>PreviousAffinity</i> to <b>NULL</b>. Before the thread exits, it calls <b>KeRevertToUserGroupAffinityThread</b> to restore the thread affinity that was saved by the first <b>KeSetSystemGroupAffinityThread</b> call.</p>

<p>The following diagram shows a somewhat different calling pattern in which pairs of <b>KeSetSystemGroupAffinityThread</b> and <b>KeRevertToUserGroupAffinityThread</b> calls are nested. In this diagram, each call to <b>KeSetSystemGroupAffinityThread</b> in the driver thread uses the <i>PreviousAffinity</i> output parameter to save the previous thread affinity, and each of these calls is paired with a call to <b>KeRevertToUserGroupAffinityThread</b> that restores the saved thread affinity.</p>

<p>In the preceding diagram, function A in the driver thread calls function B twice. Assume that on entry to function A, the thread still has the affinity assigned to it by the user-mode application. Thus, the <b>KeSetSystemGroupAffinityThread</b> call in function A saves the original, user-mode thread affinity. During the first call to function B, the <b>KeSetSystemGroupAffinityThread</b> saves the thread affinity assigned by the driver in function A, and the corresponding call to <b>KeRevertToUserGroupAffinityThread</b> restores this affinity. After B returns, the <b>KeRevertToUserGroupAffinityThread</b> in A restores the original, user-mode thread affinity. During the second call to B, the <b>KeSetSystemGroupAffinityThread</b> call saves the original, user-mode thread affinity, and the corresponding call to <b>KeRevertToUserGroupAffinityThread</b> restores this affinity. The point of this example is that function B does not need to know whether the caller (function A) changed the thread affinity to a driver-defined value before calling B.</p>

<p>If <b>KeSetSystemGroupAffinityThread</b> is called at IRQL &lt;= APC_LEVEL and the call is successful, the new group affinity takes effect immediately. When the call returns, the calling thread is already running on a processor that is specified in the new group affinity. If <b>KeSetSystemGroupAffinityThread</b> is called at IRQL = DISPATCH_LEVEL and the call is successful, the pending processor change is deferred until the caller lowers the IRQL below DISPATCH_LEVEL.</p>

<p>This routine changes the group number and group-relative affinity mask of the calling thread. The <i>Affinity</i> parameter points to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546539">GROUP_AFFINITY</a> structure. The group number and affinity mask in this structure identify a set of processors on which the thread can run. If successful, the routine schedules the thread to run on a processor in this set.</p>

<p>If the <i>PreviousAffinity</i> parameter is non-<b>NULL</b>, the routine saves information about the previous group affinity, which were in effect at the start of the call, in the <b>GROUP_AFFINITY</b> structure that <i>PreviousAffinity</i> points to. To restore the previous thread affinity, the caller can supply the pointer to this structure as an input parameter to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553195">KeRevertToUserGroupAffinityThread</a> routine.</p>

<p>In a multiprocessor system, a kernel-mode driver routine that runs in the context of a user-mode thread might need to call <b>KeSetSystemGroupAffinityThread</b> to temporarily change the group affinity of the thread. Before the routine exits, it should call <b>KeRevertToUserGroupAffinityThread</b> to restore the affinity mask of the thread to its original value.</p>

<p>A process can have affinity for more than one group at a time. However, a thread can be assigned to only one group at any time. That group is always in the affinity of the thread's process. A thread can change the group to which it is assigned by calling <b>KeSetSystemGroupAffinityThread</b>.</p>

<p><b>KeSetSystemGroupAffinityThread</b> changes the group number and affinity mask to the values that are specified in *<i>Affinity</i> only if the following are true:</p>

<p>The group number is valid.</p>

<p>The affinity mask is valid (that is, only mask bits that correspond to logical processors in the group are set).</p>

<p>At least one of the processors that is specified in the affinity mask is active. </p>

<p>If any of these conditions is not met, the group number and affinity mask of the thread remain unchanged. If <i>PreviousAffinity</i> is non-<b>NULL</b>, the routine writes zero to both the group number and the affinity mask in *<i>PreviousAffinity</i>.</p>

<p>Additionally, <b>KeSetSystemGroupAffinityThread</b> writes zero to both the group number and the affinity mask in *<i>PreviousAffinity</i> if the previous group affinity was assigned to the thread in user mode. In response to a <b>GROUP_AFFINITY</b> structure in which the group number and affinity mask are both zero, <b>KeRevertToUserGroupAffinityThread</b> restores the current user-mode thread affinity. If the user-mode thread affinity changes between the <b>KeSetSystemGroupAffinityThread</b> and <b>KeRevertToUserGroupAffinityThread</b> calls, the most recent user-mode affinity is assigned to the thread. (An application can call a function such as <a href="base.setthreadgroupaffinity">SetThreadGroupAffinity</a> to change the user-mode group affinity of a thread.)</p>

<p>Before the new affinity mask in *<i>Affinity</i> takes effect, <b>KeSetSystemGroupAffinityThread</b> removes (sets to zero) any affinity mask bits that correspond to processors that are not currently active. In a subsequent <b>KeSetSystemGroupAffinityThread</b> call, the value that the routine writes to *<i>PreviousAffinity</i> might contain an affinity mask that has been modified in this way.</p>

<p>A related routine, <a href="https://msdn.microsoft.com/library/windows/hardware/ff553271">KeSetSystemAffinityThreadEx</a>, changes the affinity mask of the calling thread, but this routine, unlike <b>KeSetSystemGroupAffinityThread</b>, does not accept a group number as an input parameter. Starting with Windows 7, <b>KeSetSystemAffinityThreadEx</b> assumes that the affinity mask refers to processors in group 0, which is compatible with the behavior of this routine in earlier versions of Windows that do not support groups. This behavior ensures that existing drivers that call <b>KeSetSystemAffinityThreadEx</b> and that use no group-oriented features will run correctly in multiprocessor systems that have two or more groups. However, drivers that use any group-oriented features in Windows 7 and later versions of the Windows operating system should call <b>KeSetSystemGroupAffinityThread</b> instead of <b>KeSetSystemAffinityThreadEx</b>.</p>

<p><b>KeSetSystemGroupAffinityThread</b> and <b>KeRevertToUserGroupAffinityThread</b> support a variety of calling patterns. Two examples are shown in the following diagrams.</p>

<p>The following diagram represents a driver thread that calls <b>KeSetSystemGroupAffinityThread</b> three times to change the thread affinity, and then calls <b>KeRevertToUserGroupAffinityThread</b> to restore the original thread affinity.</p>

<p>In the preceding diagram, the three boxes labeled "Set affinity" are calls to <b>KeSetSystemGroupAffinityThread</b>, and the box labeled "Revert affinity" is a call to <b>KeRevertToUserGroupAffinityThread</b>. The first <b>KeSetSystemGroupAffinityThread</b> call uses the <i>PreviousAffinity</i> output pointer to save the original thread affinity. In the next two calls to <b>KeSetSystemGroupAffinityThread</b> (marked with asterisks), the caller sets <i>PreviousAffinity</i> to <b>NULL</b>. Before the thread exits, it calls <b>KeRevertToUserGroupAffinityThread</b> to restore the thread affinity that was saved by the first <b>KeSetSystemGroupAffinityThread</b> call.</p>

<p>The following diagram shows a somewhat different calling pattern in which pairs of <b>KeSetSystemGroupAffinityThread</b> and <b>KeRevertToUserGroupAffinityThread</b> calls are nested. In this diagram, each call to <b>KeSetSystemGroupAffinityThread</b> in the driver thread uses the <i>PreviousAffinity</i> output parameter to save the previous thread affinity, and each of these calls is paired with a call to <b>KeRevertToUserGroupAffinityThread</b> that restores the saved thread affinity.</p>

<p>In the preceding diagram, function A in the driver thread calls function B twice. Assume that on entry to function A, the thread still has the affinity assigned to it by the user-mode application. Thus, the <b>KeSetSystemGroupAffinityThread</b> call in function A saves the original, user-mode thread affinity. During the first call to function B, the <b>KeSetSystemGroupAffinityThread</b> saves the thread affinity assigned by the driver in function A, and the corresponding call to <b>KeRevertToUserGroupAffinityThread</b> restores this affinity. After B returns, the <b>KeRevertToUserGroupAffinityThread</b> in A restores the original, user-mode thread affinity. During the second call to B, the <b>KeSetSystemGroupAffinityThread</b> call saves the original, user-mode thread affinity, and the corresponding call to <b>KeRevertToUserGroupAffinityThread</b> restores this affinity. The point of this example is that function B does not need to know whether the caller (function A) changed the thread affinity to a driver-defined value before calling B.</p>

<p>If <b>KeSetSystemGroupAffinityThread</b> is called at IRQL &lt;= APC_LEVEL and the call is successful, the new group affinity takes effect immediately. When the call returns, the calling thread is already running on a processor that is specified in the new group affinity. If <b>KeSetSystemGroupAffinityThread</b> is called at IRQL = DISPATCH_LEVEL and the call is successful, the pending processor change is deferred until the caller lowers the IRQL below DISPATCH_LEVEL.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 7.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Wdm.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL (see Remarks section).</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546539">GROUP_AFFINITY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553195">KeRevertToUserGroupAffinityThread</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553271">KeSetSystemAffinityThreadEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20KeSetSystemGroupAffinityThread routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>