---
title: sys.xml_schema_attributes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xml_schema_attributes_TSQL
- xml_schema_attributes
- sys.xml_schema_attributes_TSQL
- sys.xml_schema_attributes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_attributes catalog view
ms.assetid: dd0c98aa-5e72-4df6-96d9-482786c8dbb1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d408ae0e77676c7f13466ca83aec1e575830dbc1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901014"
---
# <a name="sysxml_schema_attributes-transact-sql"></a>sys.xml_schema_attributes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回每個 XML 架構元件的資料列，這是**symbol_space**的**屬性。**  

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**\<inherited columns>**|--|繼承自[sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md)。|  
|**is_default_fixed**|**bit**|1 = 預設值是固定值。 在 XML 執行個體中不能覆寫這個值。<br /><br /> 0 = 預設值不是屬性的固定值。 (預設值)|  
|**must_be_qualified**|**bit**|1 = 屬性必須明確限定命名空間。<br /><br /> 0 = 屬性可隱含限定命名空間。 (預設值)|  
|**default_value**|**nvarchar**<br /><br /> **（4000）**|屬性的預設值。 如果沒有提供預設值，則為 NULL。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 架構 &#40;XML 類型系統&#41; 目錄檢視 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
