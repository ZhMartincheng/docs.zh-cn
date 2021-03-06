---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7ecc70f1c4d7184401dd29908968f628f2e6792a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484209"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
指定的事务被中止，因为当会话被关闭时尚未完成，且 TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute 被设置为 false。  
  
## <a name="description"></a>描述  
 如果当前活动会话已关闭，事务未完成，并且 TransactionAutoCompleteOnSessionClose 设置为 `false`，则进行跟踪。  
  
## <a name="troubleshooting"></a>疑难解答  
 此跟踪指示一个应予调查的潜在应用程序 Bug。  
  
## <a name="see-also"></a>请参阅  
 [跟踪](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用跟踪来排除应用程序故障](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理和诊断](../../../../../docs/framework/wcf/diagnostics/index.md)
