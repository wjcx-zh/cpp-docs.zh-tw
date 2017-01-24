---
title: "CComCoClass Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComCoClass"
  - "ATL.CComCoClass"
  - "ATL::CComCoClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], aggregation models"
  - "CComCoClass class"
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCoClass Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會建立類別的執行個體並取得其屬性的方法。  
  
## 語法  
  
```  
  
      template<  
   class T,  
   const CLSID* pclsid = &CLSID_NULL  
>  
class CComCoClass  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `CComCoClass`。  
  
 *pclsid*  
 物件的 CLSID 的指標。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComCoClass::CreateInstance](../Topic/CComCoClass::CreateInstance.md)|\(靜態\) 建立類別和查詢介面的執行個體。|  
|[CComCoClass::Error](../Topic/CComCoClass::Error.md)|\(靜態\) 傳回豐富的錯誤資訊傳送至用戶端。|  
|[CComCoClass::GetObjectCLSID](../Topic/CComCoClass::GetObjectCLSID.md)|\(靜態屬性\) 會傳回物件的類別識別項。|  
|[CComCoClass::GetObjectDescription](../Topic/CComCoClass::GetObjectDescription.md)|\(傳回物件之描述的靜態\) 覆寫。|  
  
## 備註  
 `CComCoClass` 用來擷取物件的 CLSID，將錯誤訊息並建立類別的執行個體的方法。  要從 `CComCoClass`衍生自 [物件對應](http://msdn.microsoft.com/zh-tw/b57619cc-534f-4b8f-bfd4-0c12f937202f) 註冊的任何類別。  
  
 `CComCoClass` 也定義預設的 Class Factory 和您的物件模型中的彙總。  `CComCoClass` 使用下列兩個巨集:  
  
-   [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md) 宣告 Class Factory 是 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)。  
  
-   [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md) 宣告您的物件可彙總。  
  
 您可以指定另一個巨集覆寫這些預設值是在您的類別定義。  例如，使用 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 而不是 `CComClassFactory`，請指定 [DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 巨集:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/CPP/ccomcoclass-class_1.h)]  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)