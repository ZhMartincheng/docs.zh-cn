---
title: 数学规范函数
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9d823eb45babca4b8f5dd717b4fb92c1984d1c8c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765095"
---
# <a name="math-canonical-functions"></a>数学规范函数
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供了数学规范函数。  
  
 下表显示 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 数学规范函数。  
  
|函数|描述|  
|--------------|-----------------|  
|`Abs(` `value` `)`|返回 `value` 的绝对值。<br /><br /> **参数**<br /><br /> `Int16`， `Int32`， `Int64`， `Byte`， `Single`， `Double`，和`Decimal`。<br /><br /> **返回值**<br /><br /> `value` 的类型。<br /><br /> **示例**<br /><br /> `Abs(-2)`|  
|`Ceiling(` `value` `)`|返回不小于 `value` 的最小整数。<br /><br /> **参数**<br /><br /> A `Single`， `Double`，和`Decimal`。<br /><br /> **返回值**<br /><br /> `value` 的类型。<br /><br /> **示例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(` `value` `)`|返回不大于 `value` 的最大整数。<br /><br /> **参数**<br /><br /> A `Single`， `Double`，和`Decimal`。<br /><br /> **返回值**<br /><br /> `value` 的类型。<br /><br /> **示例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|返回对指定的 `value` 求指定的 `exponent` 幂次所得的结果。<br /><br /> **参数**<br /><br /> `value`： 一个`Int32, Int64, Double`，或`Decimal`。<br /><br /> `exponent`： 一个`Int64``, Double`，或`Decimal`。<br /><br /> **返回值**<br /><br /> `value` 的类型。<br /><br /> **示例**<br /><br /> `Power(748.58,2)`|  
|`Round(` `value` `)`|返回 `value` 的整数部分，舍入到最近的整数。<br /><br /> **参数**<br /><br /> A `Single`， `Double`，和`Decimal`。<br /><br /> **返回值**<br /><br /> `value` 的类型。<br /><br /> **示例**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|返回 `value`，舍入到最近的指定 `digits`。<br /><br /> **参数**<br /><br /> `value`：`Double` 或 `Decimal`。<br /><br /> `digits`：`Int16` 或 `Int32`。<br /><br /> **返回值**<br /><br /> `value` 的类型。<br /><br /> **示例**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|返回 `value`，截断至最近的指定 `digits`。<br /><br /> **参数**<br /><br /> `value`：`Double` 或 `Decimal`。<br /><br /> `digits`：`Int16` 或 `Int32`。<br /><br /> **返回值**<br /><br /> `value` 的类型。<br /><br /> **示例**<br /><br /> `Truncate(748.58,1)`|  
  
 如果提供 `null` 输入，则这些函数返回 `null`。  
  
 Microsoft SQL 客户端托管提供程序中提供了等效功能。 有关详细信息，请参阅[用于实体框架函数的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="see-also"></a>请参阅  
 [规范函数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
