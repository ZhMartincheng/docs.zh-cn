---
title: "ICorDebugManagedCallback2::Exception 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a78900a6e37c3ae136489c35da7b0cd2931f24a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="088b3-102">ICorDebugManagedCallback2::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="088b3-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="088b3-103">通知调试器搜索异常处理程序已开始。</span><span class="sxs-lookup"><span data-stu-id="088b3-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="088b3-104">语法</span><span class="sxs-lookup"><span data-stu-id="088b3-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="088b3-105">参数</span><span class="sxs-lookup"><span data-stu-id="088b3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="088b3-106">[in]指向一个表示包含引发异常的线程的应用程序域的 ICorDebugAppDomain 对象的指针。</span><span class="sxs-lookup"><span data-stu-id="088b3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="088b3-107">[in]指向一个 ICorDebugThread 对象，表示引发异常的线程的指针。</span><span class="sxs-lookup"><span data-stu-id="088b3-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="088b3-108">[in]指向根据所表示的帧，ICorDebugFrame 对象的指针`dwEventType`参数。</span><span class="sxs-lookup"><span data-stu-id="088b3-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="088b3-109">有关详细信息，请参阅备注部分中的表。</span><span class="sxs-lookup"><span data-stu-id="088b3-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="088b3-110">[in]一个整数，指定偏移量，所确定的那样`dwEventType`参数。</span><span class="sxs-lookup"><span data-stu-id="088b3-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="088b3-111">有关详细信息，请参阅备注部分中的表。</span><span class="sxs-lookup"><span data-stu-id="088b3-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="088b3-112">[in]CorDebugExceptionCallbackType 枚举，指定此异常回调的类型的值。</span><span class="sxs-lookup"><span data-stu-id="088b3-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="088b3-113">[in]值为[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)枚举，它指定有关异常的其他信息</span><span class="sxs-lookup"><span data-stu-id="088b3-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="088b3-114">备注</span><span class="sxs-lookup"><span data-stu-id="088b3-114">Remarks</span></span>  
 <span data-ttu-id="088b3-115">`Exception`异常处理过程的搜索阶段在不同时刻调用回调。</span><span class="sxs-lookup"><span data-stu-id="088b3-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="088b3-116">即，它可以调用多个一次而展开异常。</span><span class="sxs-lookup"><span data-stu-id="088b3-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="088b3-117">正在处理的异常可以从所引用的 ICorDebugThread 对象检索`pThread`参数。</span><span class="sxs-lookup"><span data-stu-id="088b3-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="088b3-118">由特定帧和偏移量`dwEventType`参数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="088b3-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="088b3-119">`dwEventType` 的值</span><span class="sxs-lookup"><span data-stu-id="088b3-119">Value of `dwEventType`</span></span>|<span data-ttu-id="088b3-120">`pFrame` 的值</span><span class="sxs-lookup"><span data-stu-id="088b3-120">Value of `pFrame`</span></span>|<span data-ttu-id="088b3-121">`nOffset` 的值</span><span class="sxs-lookup"><span data-stu-id="088b3-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="088b3-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="088b3-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="088b3-123">引发异常的帧。</span><span class="sxs-lookup"><span data-stu-id="088b3-123">The frame that threw the exception.</span></span>|<span data-ttu-id="088b3-124">指令指针的帧中。</span><span class="sxs-lookup"><span data-stu-id="088b3-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="088b3-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="088b3-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="088b3-126">引发的异常点最接近的用户代码帧。</span><span class="sxs-lookup"><span data-stu-id="088b3-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="088b3-127">指令指针的帧中。</span><span class="sxs-lookup"><span data-stu-id="088b3-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="088b3-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="088b3-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="088b3-129">包含 catch 处理程序的帧。</span><span class="sxs-lookup"><span data-stu-id="088b3-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="088b3-130">Catch 处理程序的开头的 Microsoft 中间语言 (MSIL) 偏移量。</span><span class="sxs-lookup"><span data-stu-id="088b3-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="088b3-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="088b3-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="088b3-132">NULL</span><span class="sxs-lookup"><span data-stu-id="088b3-132">NULL</span></span>|<span data-ttu-id="088b3-133">未定义。</span><span class="sxs-lookup"><span data-stu-id="088b3-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="088b3-134">要求</span><span class="sxs-lookup"><span data-stu-id="088b3-134">Requirements</span></span>  
 <span data-ttu-id="088b3-135">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="088b3-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="088b3-136">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="088b3-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="088b3-137">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="088b3-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="088b3-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="088b3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="088b3-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="088b3-139">See Also</span></span>  
 [<span data-ttu-id="088b3-140">ICorDebugManagedCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="088b3-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="088b3-141">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="088b3-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)