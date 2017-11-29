---
title: Serialization1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e63428400a7868b71a2d8e52637e4b22e4c44ee7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="serialization"></a><span data-ttu-id="0ceff-102">序列化</span><span class="sxs-lookup"><span data-stu-id="0ceff-102">Serialization</span></span>
<span data-ttu-id="0ceff-103">序列化是将对象转换为一种格式，可以随时保存或传输的过程。</span><span class="sxs-lookup"><span data-stu-id="0ceff-103">Serialization is the process of converting an object into a format that can be readily persisted or transported.</span></span> <span data-ttu-id="0ceff-104">例如，你可以将对象序列化，传输通过 Internet 使用 HTTP，和目标计算机上反其序列化。</span><span class="sxs-lookup"><span data-stu-id="0ceff-104">For example, you can serialize an object, transport it over the Internet using HTTP, and deserialized it at the destination machine.</span></span>  
  
 <span data-ttu-id="0ceff-105">.NET Framework 提供了针对各种序列化方案进行了优化的三个主要的序列化技术。</span><span class="sxs-lookup"><span data-stu-id="0ceff-105">The .NET Framework offers three main serialization technologies optimized for various serialization scenarios.</span></span> <span data-ttu-id="0ceff-106">下表列出了这些技术以及与这些技术相关的主要 Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="0ceff-106">The following table lists these technologies and the main Framework types related to these technologies.</span></span>  
  
|<span data-ttu-id="0ceff-107">**技术名称**</span><span class="sxs-lookup"><span data-stu-id="0ceff-107">**Technology Name**</span></span>|<span data-ttu-id="0ceff-108">**主要类型**</span><span class="sxs-lookup"><span data-stu-id="0ceff-108">**Main Types**</span></span>|<span data-ttu-id="0ceff-109">**方案**</span><span class="sxs-lookup"><span data-stu-id="0ceff-109">**Scenarios**</span></span>|  
|-------------------------|--------------------|-------------------|  
|<span data-ttu-id="0ceff-110">**数据协定序列化**</span><span class="sxs-lookup"><span data-stu-id="0ceff-110">**Data Contract Serialization**</span></span>|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|<span data-ttu-id="0ceff-111">常规持久性</span><span class="sxs-lookup"><span data-stu-id="0ceff-111">General persistence</span></span><br /><span data-ttu-id="0ceff-112">Web 服务</span><span class="sxs-lookup"><span data-stu-id="0ceff-112">Web Services</span></span><br /><span data-ttu-id="0ceff-113">JSON</span><span class="sxs-lookup"><span data-stu-id="0ceff-113">JSON</span></span>|  
|<span data-ttu-id="0ceff-114">**XML 序列化**</span><span class="sxs-lookup"><span data-stu-id="0ceff-114">**XML Serialization**</span></span>|<xref:System.Xml.Serialization.XmlSerializer>|<span data-ttu-id="0ceff-115">具有完全控制权限的 XML 形状的 XML 格式</span><span class="sxs-lookup"><span data-stu-id="0ceff-115">XML format with full control over the shape of the XML</span></span>|  
|<span data-ttu-id="0ceff-116">**运行时序列化 （二进制和 SOAP）**</span><span class="sxs-lookup"><span data-stu-id="0ceff-116">**Runtime Serialization (Binary and SOAP)**</span></span>|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|<span data-ttu-id="0ceff-117">.NET 远程处理</span><span class="sxs-lookup"><span data-stu-id="0ceff-117">.NET Remoting</span></span>|  
  
 <span data-ttu-id="0ceff-118">**✓ 执行**思考设计新类型时序列化。</span><span class="sxs-lookup"><span data-stu-id="0ceff-118">**✓ DO** think about serialization when you design new types.</span></span>  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a><span data-ttu-id="0ceff-119">选择要支持的合适的序列化技术</span><span class="sxs-lookup"><span data-stu-id="0ceff-119">Choosing the Right Serialization Technology to Support</span></span>  
 <span data-ttu-id="0ceff-120">**请考虑 ✓**支持数据协定序列化，如果类型的实例可能需要保留或在 Web 服务中使用。</span><span class="sxs-lookup"><span data-stu-id="0ceff-120">**✓ CONSIDER** supporting Data Contract Serialization if instances of your type might need to be persisted or used in Web Services.</span></span>  
  
 <span data-ttu-id="0ceff-121">**请考虑 ✓**支持 XML 序列化而非或除了数据协定序列化，如果你需要更好地控制类型序列化时，会产生的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="0ceff-121">**✓ CONSIDER** supporting the XML Serialization instead of or in addition to Data Contract Serialization if you need more control over the XML format that is produced when the type is serialized.</span></span>  
  
 <span data-ttu-id="0ceff-122">这可能需要在某些互操作性方案需要使用 XML 构造不支持数据协定序列化，例如，若要生成的 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="0ceff-122">This may be necessary in some interoperability scenarios where you need to use an XML construct that is not supported by Data Contract Serialization, for example, to produce XML attributes.</span></span>  
  
 <span data-ttu-id="0ceff-123">**请考虑 ✓**支持运行时序列化，如果需要穿越.NET 远程处理边界类型的实例。</span><span class="sxs-lookup"><span data-stu-id="0ceff-123">**✓ CONSIDER** supporting the Runtime Serialization if instances of your type need to travel across .NET Remoting boundaries.</span></span>  
  
 <span data-ttu-id="0ceff-124">**请避免 x**只是为了常规持久性原因支持运行时序列化或 XML 序列化。</span><span class="sxs-lookup"><span data-stu-id="0ceff-124">**X AVOID** supporting Runtime Serialization or XML Serialization just for general persistence reasons.</span></span> <span data-ttu-id="0ceff-125">而是希望数据协定序列化。</span><span class="sxs-lookup"><span data-stu-id="0ceff-125">Prefer Data Contract Serialization instead.</span></span>  
  
## <a name="supporting-data-contract-serialization"></a><span data-ttu-id="0ceff-126">支持数据协定序列化</span><span class="sxs-lookup"><span data-stu-id="0ceff-126">Supporting Data Contract Serialization</span></span>  
 <span data-ttu-id="0ceff-127">类型都可以通过应用支持数据协定序列化<xref:System.Runtime.Serialization.DataContractAttribute>为的类型和<xref:System.Runtime.Serialization.DataMemberAttribute>类型的成员 （字段和属性）。</span><span class="sxs-lookup"><span data-stu-id="0ceff-127">Types can support Data Contract Serialization by applying the <xref:System.Runtime.Serialization.DataContractAttribute> to the type and the <xref:System.Runtime.Serialization.DataMemberAttribute> to the members (fields and properties) of the type.</span></span>  
  
 <span data-ttu-id="0ceff-128">**请考虑 ✓**标记的类型公共数据成员，如果可以在部分信任环境中使用该类型。</span><span class="sxs-lookup"><span data-stu-id="0ceff-128">**✓ CONSIDER** marking data members of your type public if the type can be used in partial trust.</span></span>  
  
 <span data-ttu-id="0ceff-129">在完全信任，数据协定序列化程序进行序列化和反序列化非公共类型和成员，但可以序列化和反序列化在部分信任环境中只有公共成员。</span><span class="sxs-lookup"><span data-stu-id="0ceff-129">In full trust, Data Contract serializers can serialize and deserialize nonpublic types and members, but only public members can be serialized and deserialized in partial trust.</span></span>  
  
 <span data-ttu-id="0ceff-130">**✓ 执行**实现具有的所有属性的 getter 和 setter <xref:System.Runtime.Serialization.DataMemberAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0ceff-130">**✓ DO** implement a getter and setter on all properties that have <xref:System.Runtime.Serialization.DataMemberAttribute>.</span></span> <span data-ttu-id="0ceff-131">数据协定序列化程序需要 getter 和 setter 要被视为可序列化的类型。</span><span class="sxs-lookup"><span data-stu-id="0ceff-131">Data Contract serializers require both the getter and the setter for the type to be considered serializable.</span></span> <span data-ttu-id="0ceff-132">（在.NET Framework 3.5 SP1 中，一些集合属性可以是仅。）如果不会在部分信任模式下使用类型，则这两个属性访问器中的一个或两个都可以是非公共的。</span><span class="sxs-lookup"><span data-stu-id="0ceff-132">(In .NET Framework 3.5 SP1, some collection properties can be get-only.) If the type won’t be used in partial trust, one or both of the property accessors can be nonpublic.</span></span>  
  
 <span data-ttu-id="0ceff-133">**请考虑 ✓**的反序列化的实例初始化使用序列化回调。</span><span class="sxs-lookup"><span data-stu-id="0ceff-133">**✓ CONSIDER** using the serialization callbacks for initialization of deserialized instances.</span></span>  
  
 <span data-ttu-id="0ceff-134">反序列化对象时，不调用任何构造函数。</span><span class="sxs-lookup"><span data-stu-id="0ceff-134">Constructors are not called when objects are deserialized.</span></span> <span data-ttu-id="0ceff-135">（有例外规则。</span><span class="sxs-lookup"><span data-stu-id="0ceff-135">(There are exceptions to the rule.</span></span> <span data-ttu-id="0ceff-136">集合的构造函数标记有<xref:System.Runtime.Serialization.CollectionDataContractAttribute>在反序列化过程中调用。)因此，在正常构造过程中执行的任何逻辑需要作为一个序列化回调实现。</span><span class="sxs-lookup"><span data-stu-id="0ceff-136">Constructors of collections marked with <xref:System.Runtime.Serialization.CollectionDataContractAttribute> are called during deserialization.) Therefore, any logic that executes during normal construction needs to be implemented as one of the serialization callbacks.</span></span>  
  
 <span data-ttu-id="0ceff-137">`OnDeserializedAttribute`是最常使用的回调属性。</span><span class="sxs-lookup"><span data-stu-id="0ceff-137">`OnDeserializedAttribute` is the most commonly used callback attribute.</span></span> <span data-ttu-id="0ceff-138">此系列中的其他属性还有 <xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute> 和 <xref:System.Runtime.Serialization.OnSerializedAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0ceff-138">The other attributes in the family are <xref:System.Runtime.Serialization.OnDeserializingAttribute>,  <xref:System.Runtime.Serialization.OnSerializingAttribute>, and <xref:System.Runtime.Serialization.OnSerializedAttribute>.</span></span> <span data-ttu-id="0ceff-139">这些属性可分别用来标记在反序列化之前、序列化之前以及序列化之后执行的回调。</span><span class="sxs-lookup"><span data-stu-id="0ceff-139">They can be used to mark callbacks that get executed before deserialization, before serialization, and finally, after serialization, respectively.</span></span>  
  
 <span data-ttu-id="0ceff-140">**请考虑 ✓**使用<xref:System.Runtime.Serialization.KnownTypeAttribute>以指示反序列化复杂对象图时，应使用的具体类型。</span><span class="sxs-lookup"><span data-stu-id="0ceff-140">**✓ CONSIDER** using the <xref:System.Runtime.Serialization.KnownTypeAttribute> to indicate concrete types that should be used when deserializing a complex object graph.</span></span>  
  
 <span data-ttu-id="0ceff-141">**✓ 执行**考虑向后和向前兼容性，当创建或更改可序列化类型。</span><span class="sxs-lookup"><span data-stu-id="0ceff-141">**✓ DO** consider backward and forward compatibility when creating or changing serializable types.</span></span>  
  
 <span data-ttu-id="0ceff-142">请记住，类型的未来版本的序列化流可反序列化到类型的当前版本，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="0ceff-142">Keep in mind that serialized streams of future versions of your type can be deserialized into the current version of the type, and vice versa.</span></span>  
  
 <span data-ttu-id="0ceff-143">请确保你了解数据成员，甚至私有和内部，无法更改其名称、 类型，或者即使它们在类型的将来版本中的顺序，除非特别注意执行保留使用显式数据协定特性参数的协定.</span><span class="sxs-lookup"><span data-stu-id="0ceff-143">Make sure you understand that data members, even private and internal, cannot change their names, types, or even their order in future versions of the type unless special care is taken to preserve the contract using explicit parameters to the data contract attributes.</span></span>  
  
 <span data-ttu-id="0ceff-144">当对可序列化类型进行更改，则测试序列化的兼容的性。</span><span class="sxs-lookup"><span data-stu-id="0ceff-144">Test compatibility of serialization when making changes to serializable types.</span></span> <span data-ttu-id="0ceff-145">尝试将新版本反序列化为旧版本，以及将旧版本反序列化为新版本。</span><span class="sxs-lookup"><span data-stu-id="0ceff-145">Try deserializing the new version into an old version, and vice versa.</span></span>  
  
 <span data-ttu-id="0ceff-146">**请考虑 ✓**实现<xref:System.Runtime.Serialization.IExtensibleDataObject>以允许类型的不同版本之间的往返。</span><span class="sxs-lookup"><span data-stu-id="0ceff-146">**✓ CONSIDER** implementing <xref:System.Runtime.Serialization.IExtensibleDataObject> to allow round-tripping between different versions of the type.</span></span>  
  
 <span data-ttu-id="0ceff-147">序列化程序可通过此接口确保在往返期间不丢失任何数据。</span><span class="sxs-lookup"><span data-stu-id="0ceff-147">The interface allows the serializer to ensure that no data is lost during round-tripping.</span></span> <span data-ttu-id="0ceff-148"><xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>属性用来存储到最新版本，未知的类型的将来版本中的任何数据，因此它不能将其存储在其数据成员。</span><span class="sxs-lookup"><span data-stu-id="0ceff-148">The <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> property is used to store any data from the future version of the type that is unknown to the current version, and so it cannot store it in its data members.</span></span> <span data-ttu-id="0ceff-149">在当前版本是随后序列化和反序列化为的未来版本，附加的数据将可序列化流中。</span><span class="sxs-lookup"><span data-stu-id="0ceff-149">When the current version is subsequently serialized and deserialized into a future version, the additional data will be available in the serialized stream.</span></span>  
  
## <a name="supporting-xml-serialization"></a><span data-ttu-id="0ceff-150">支持 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="0ceff-150">Supporting XML Serialization</span></span>  
 <span data-ttu-id="0ceff-151">数据协定序列化是 main （默认值） 序列化技术在.NET Framework 中，但存在数据协定序列化不支持的序列化方案。</span><span class="sxs-lookup"><span data-stu-id="0ceff-151">Data Contract Serialization is the main (default) serialization technology in the .NET Framework, but there are serialization scenarios that Data Contract Serialization does not support.</span></span> <span data-ttu-id="0ceff-152">例如，数据协定序列化无法让您完全控制序列化程序生成或使用的 XML 的形状。</span><span class="sxs-lookup"><span data-stu-id="0ceff-152">For example, it does not give you full control over the shape of XML produced or consumed by the serializer.</span></span> <span data-ttu-id="0ceff-153">如果此类进行精细控制是必需的 XML 序列化具有要使用，并且需要设计你的类型来支持此序列化技术。</span><span class="sxs-lookup"><span data-stu-id="0ceff-153">If such fine control is required, XML Serialization has to be used, and you need to design your types to support this serialization technology.</span></span>  
  
 <span data-ttu-id="0ceff-154">**请避免 x**专门为 XML 序列化设计你的类型，除非你有非常强的原因，若要控制 XML 的形状的生成。</span><span class="sxs-lookup"><span data-stu-id="0ceff-154">**X AVOID** designing your types specifically for XML Serialization, unless you have a very strong reason to control the shape of the XML produced.</span></span> <span data-ttu-id="0ceff-155">此序列化技术已由上一节讨论的数据协定序列化所取代。</span><span class="sxs-lookup"><span data-stu-id="0ceff-155">This serialization technology has been superseded by the Data Contract Serialization discussed in the previous section.</span></span>  
  
 <span data-ttu-id="0ceff-156">**请考虑 ✓**实现<xref:System.Xml.Serialization.IXmlSerializable>接口如果你想甚至更好地控制的序列化的 XML 形状比什么所提供的应用的 XML 序列化属性。</span><span class="sxs-lookup"><span data-stu-id="0ceff-156">**✓ CONSIDER** implementing the <xref:System.Xml.Serialization.IXmlSerializable> interface if you want even more control over the shape of the serialized XML than what’s offered by applying the XML Serialization attributes.</span></span> <span data-ttu-id="0ceff-157">两种方法的接口，<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>和<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>，允许你完全控制的序列化的 XML 流。</span><span class="sxs-lookup"><span data-stu-id="0ceff-157">Two methods of the interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, allow you to fully control the serialized XML stream.</span></span> <span data-ttu-id="0ceff-158">你还可以控制获取通过将应用生成类型的 XML 架构`XmlSchemaProviderAttribute`。</span><span class="sxs-lookup"><span data-stu-id="0ceff-158">You can also control the XML schema that gets generated for the type by applying the `XmlSchemaProviderAttribute`.</span></span>  
  
## <a name="supporting-runtime-serialization"></a><span data-ttu-id="0ceff-159">支持运行时序列化</span><span class="sxs-lookup"><span data-stu-id="0ceff-159">Supporting Runtime Serialization</span></span>  
 <span data-ttu-id="0ceff-160">运行时序列化是使用.NET 远程处理技术。</span><span class="sxs-lookup"><span data-stu-id="0ceff-160">Runtime Serialization is a technology used by .NET Remoting.</span></span> <span data-ttu-id="0ceff-161">如果您认为您的类型将使用.NET 远程处理进行传输，你需要确保它们支持运行时序列化。</span><span class="sxs-lookup"><span data-stu-id="0ceff-161">If you think your types will be transported using .NET Remoting, you need to make sure they support Runtime Serialization.</span></span>  
  
 <span data-ttu-id="0ceff-162">可以通过应用提供对运行时序列化的基本支持<xref:System.SerializableAttribute>，并且更高级的方案涉及实现简单的运行时可序列化模式 (实现<xref:System.Runtime.Serialization.ISerializable>并提供序列化构造函数)。</span><span class="sxs-lookup"><span data-stu-id="0ceff-162">The basic support for Runtime Serialization can be provided by applying the <xref:System.SerializableAttribute>, and more advanced scenarios involve implementing a simple Runtime Serializable Pattern (implement <xref:System.Runtime.Serialization.ISerializable> and provide serialization constructor).</span></span>  
  
 <span data-ttu-id="0ceff-163">**请考虑 ✓**支持运行时序列化，如果在你的类型将使用.NET 远程处理。</span><span class="sxs-lookup"><span data-stu-id="0ceff-163">**✓ CONSIDER** supporting Runtime Serialization if your types will be used with .NET Remoting.</span></span> <span data-ttu-id="0ceff-164">例如，<xref:System.AddIn?displayProperty=nameWithType>命名空间使用.NET 远程处理，并因此所有类型之间都交换`System.AddIn`外接程序需要支持运行时序列化。</span><span class="sxs-lookup"><span data-stu-id="0ceff-164">For example, the <xref:System.AddIn?displayProperty=nameWithType> namespace uses .NET Remoting, and so all types exchanged between `System.AddIn` add-ins need to support Runtime Serialization.</span></span>  
  
 <span data-ttu-id="0ceff-165">**请考虑 ✓**实现运行时可序列化模式，如果你想要完成控制序列化过程。</span><span class="sxs-lookup"><span data-stu-id="0ceff-165">**✓ CONSIDER** implementing the Runtime Serializable Pattern if you want complete control over the serialization process.</span></span> <span data-ttu-id="0ceff-166">例如，如果您需要在对数据进行序列化或反序列化时转换数据。</span><span class="sxs-lookup"><span data-stu-id="0ceff-166">For example, if you want to transform data as it gets serialized or deserialized.</span></span>  
  
 <span data-ttu-id="0ceff-167">此模式非常简单。</span><span class="sxs-lookup"><span data-stu-id="0ceff-167">The pattern is very simple.</span></span> <span data-ttu-id="0ceff-168">您需要执行的全部操作就是实现 <xref:System.Runtime.Serialization.ISerializable> 接口，并提供在反序列化对象时使用的特殊构造函数。</span><span class="sxs-lookup"><span data-stu-id="0ceff-168">All you need to do is implement the <xref:System.Runtime.Serialization.ISerializable> interface and provide a special constructor that is used when the object is deserialized.</span></span>  
  
 <span data-ttu-id="0ceff-169">**✓ 执行**做出受保护的序列化构造函数并提供两个参数类型和名为在以下部分的示例所示完全一样。</span><span class="sxs-lookup"><span data-stu-id="0ceff-169">**✓ DO** make the serialization constructor protected and provide two parameters typed and named exactly as shown in the sample here.</span></span>  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="0ceff-170">**✓ 执行**实现`ISerializable`成员显式。</span><span class="sxs-lookup"><span data-stu-id="0ceff-170">**✓ DO** implement the `ISerializable` members explicitly.</span></span>  
  
 <span data-ttu-id="0ceff-171">**✓ 执行**应用到的链接要求<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType>实现。</span><span class="sxs-lookup"><span data-stu-id="0ceff-171">**✓ DO** apply a link demand to <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="0ceff-172">这可确保仅完全受信任的核心应用程序和运行时序列化程序有权访问该成员。</span><span class="sxs-lookup"><span data-stu-id="0ceff-172">This ensures that only fully trusted core and the Runtime Serializer have access to the member.</span></span>  
  
 <span data-ttu-id="0ceff-173">*部分 © 2005年，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="0ceff-173">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0ceff-174">*通过从皮尔逊教育版，Inc.的权限重新打印[Framework 设计准则： 约定、 语法和可重用.NET 库，版本 2 的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)通过 Krzysztof Cwalina 和 Brad Abrams，发布 2008 年 10 月 22，通过Microsoft Windows 开发系列的一部分的 Addison Wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="0ceff-174">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ceff-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ceff-175">See Also</span></span>  
 [<span data-ttu-id="0ceff-176">框架设计指南</span><span class="sxs-lookup"><span data-stu-id="0ceff-176">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="0ceff-177">使用准则</span><span class="sxs-lookup"><span data-stu-id="0ceff-177">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)