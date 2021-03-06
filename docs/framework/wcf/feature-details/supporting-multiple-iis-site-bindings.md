---
title: 支持多个 IIS 站点绑定
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 9b92243bb7aaea5c8ecf708ce863e6979bc9f17c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497615"
---
# <a name="supporting-multiple-iis-site-bindings"></a>支持多个 IIS 站点绑定
当承载 Windows Communication Foundation (WCF) 服务在 Internet 信息服务 (IIS) 7.0 时，你可能想要提供同一站点使用相同协议的多个基址。 这使得同一服务可以响应多个不同的 URI。 这是有用的当你想要承载的服务在其侦听时http://www.contoso.com和http://contoso.com。在创建对于内部用户和外部用户使用不同基址的服务时，此功能也非常有用。 例如：http://internal.contoso.com和http://www.contoso.com。  
  
> [!NOTE]
>  此功能仅在使用 HTTP 协议时可用。  
  
## <a name="multiple-base-addresses"></a>多个基址  
 此功能才可用在 IIS 下承载的 WCF 服务。 默认情况下不启用此功能。 若要启用它必须添加`multipleSiteBindingsEnabled`属性设为 <`serviceHostingEnvironment`> 元素在 Web.config 文件并将其设置为`true`，下面的示例中所示。  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 当承载在 IIS 下的 WCF 服务时，IIS 会根据包含应用程序的虚拟目录的 URI 为你创建一个基址。 你可以通过 Internet 信息服务管理器添加使用相同协议的其他基址，从而向网站添加一个或多个绑定。 对于每个绑定，请指定协议（HTTP 或 HTTPS）、IP 地址、端口和主机名。 有关使用 Internet Information Services 管理器的详细信息，请参阅[IIS 管理器 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057)。 有关将绑定添加到站点的详细信息，请参阅[创建网站 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 指定的同一站点的多个基址会影响 WCF 帮助页中，导入架构和由服务生成的 WSDL/MEX 信息的内容。 WCF 帮助页显示的命令行使用来生成 WCF 客户端可以与服务进行通信。 此命令行只包含在 IIS 绑定中为网站指定的第一个地址。 与导入方案时相似，只使用在 IIS 绑定中指定的第一个基址。 WSDL 和 MEX 数据包含在 IIS 绑定中指定的所有基址。  
  
> [!WARNING]
>  这意味着，如果某个服务有两个基址，其中一个供内部用户使用，另一个供外部用户使用，将在由该服务生成的 WSDL/MEX 信息中指定这两个基址。
