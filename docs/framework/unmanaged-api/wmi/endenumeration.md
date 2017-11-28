---
title: "EndEnumeration 函数 （非托管 API 参考）"
description: "EndEnumeration 函数将终止枚举。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: EndEnumeration
helpviewer_keywords: EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 043fce26870e5af2850b9f2e91e7e97c7bee6c90
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="f3ebb-103">EndEnumeration 函数</span><span class="sxs-lookup"><span data-stu-id="f3ebb-103">EndEnumeration function</span></span>
<span data-ttu-id="f3ebb-104">终止通过调用启动枚举序列[BeginEnumeration 函数](beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f3ebb-105">语法</span><span class="sxs-lookup"><span data-stu-id="f3ebb-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f3ebb-106">参数</span><span class="sxs-lookup"><span data-stu-id="f3ebb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f3ebb-107">[in]未使用此参数。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f3ebb-108">[in]指向的指针[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)实例。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="f3ebb-109">返回值</span><span class="sxs-lookup"><span data-stu-id="f3ebb-109">Return value</span></span>

<span data-ttu-id="f3ebb-110">此函数返回以下值中定义*WbemCli.h*标头文件，或者你可以定义它们常量作为在代码中：</span><span class="sxs-lookup"><span data-stu-id="f3ebb-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f3ebb-111">返回的常量</span><span class="sxs-lookup"><span data-stu-id="f3ebb-111">Constant</span></span>  |<span data-ttu-id="f3ebb-112">值</span><span class="sxs-lookup"><span data-stu-id="f3ebb-112">Value</span></span>  |<span data-ttu-id="f3ebb-113">描述</span><span class="sxs-lookup"><span data-stu-id="f3ebb-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="f3ebb-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f3ebb-114">0x80041001</span></span> | <span data-ttu-id="f3ebb-115">发生了常规错误。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f3ebb-116">0</span><span class="sxs-lookup"><span data-stu-id="f3ebb-116">0</span></span> | <span data-ttu-id="f3ebb-117">函数调用成功。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f3ebb-118">备注</span><span class="sxs-lookup"><span data-stu-id="f3ebb-118">Remarks</span></span>

<span data-ttu-id="f3ebb-119">此函数包装对的调用[IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="f3ebb-120">调用`EndEnumeration`函数不是必需的但它建议，因为它会释放枚举与关联的资源。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="f3ebb-121">但是，resoruces 后被释放自动启动下一步枚举或释放的对象。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="f3ebb-122">要求</span><span class="sxs-lookup"><span data-stu-id="f3ebb-122">Requirements</span></span>  
 <span data-ttu-id="f3ebb-123">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ebb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ebb-124">**标头：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f3ebb-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f3ebb-125">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ebb-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ebb-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3ebb-126">See also</span></span>  
[<span data-ttu-id="f3ebb-127">WMI 和性能计数器 （非托管 API 参考）</span><span class="sxs-lookup"><span data-stu-id="f3ebb-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)