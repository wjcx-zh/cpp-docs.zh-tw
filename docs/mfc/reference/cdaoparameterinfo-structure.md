---
title: "CDaoParameterInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoParameterInfo 結構"
  - "DAO (資料存取物件), Parameters 集合"
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoParameterInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoParameterInfo` 結構包含為資料存取物件 \(DAO\) 定義的參數物件之資訊。  
  
## 語法  
  
```  
  
      struct CDaoParameterInfo  
{  
   CString m_strName;       // Primary  
   short m_nType;           // Primary  
   ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一命名參數物件。  如需詳細資訊，請參閱 DAO 幫助中的「名字屬性」主題。  
  
 `m_nType`  
 表示參數物件的資料型別的值。  如需可能值的清單，請參閱 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 結構的 `m_nType` 成員。  如需詳細資訊，請參閱 DAO 幫助中的「型別屬性」主題。  
  
 *m\_varValue*  
 參數的值，儲存在 [COleVariant](../../mfc/reference/colevariant-class.md) 物件。  
  
## 備註  
 對主要和次要的參考指示出在類別 `CDaoQueryDef` 中，[GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md) 成員函式如何傳回資訊。  
  
 MFC 不封裝類別中的 DAO 參數物件。  DAO querydef 物件基礎 MFC `CDaoQueryDef` 物件將參數儲存在參數集合中。  若要存取 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 物件內的參數物件，請呼叫特定參數名稱的 querydef 物件之 `GetParameterInfo` 成員函式，或參數集合內的索引。  您可以將 [CDaoQueryDef::GetParameterCount](../Topic/CDaoQueryDef::GetParameterCount.md) 成員函式與 `GetParameterInfo` 一起使用，在參數集合中執行迴圈。  
  
 [CDaoQueryDef::GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md) 成員函式擷取的資訊儲存在 `CDaoParameterInfo` 結構中。  為參數物件儲存的參數集合呼叫 querydef 物件的 `GetParameterInfo`。  
  
> [!NOTE]
>  如果您要取得或設定參數的值，請使用類別 `CDaoRecordset`的 [GetParamValue](../Topic/CDaoRecordset::GetParamValue.md) 和 [SetParamValue](../Topic/CDaoRecordset::SetParamValue.md) 成員函式。  
  
 `CDaoParameterInfo` 也會在偵錯組建中定義一個 `Dump` 成員函式。  您可以使用 `Dump` 來傾印 `CDaoParameterInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)