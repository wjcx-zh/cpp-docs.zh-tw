---
title: "COleVariant Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation, 參數型別"
  - "COleVariant class"
  - "VARIANT data type"
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 [Variant](http://msdn.microsoft.com/zh-tw/e305240e-9e11-4006-98cc-26f4932d2118) 資料型別。  
  
## 語法  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleVariant::COleVariant](../Topic/COleVariant::COleVariant.md)|建構 `COleVariant` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleVariant::Attach](../Topic/COleVariant::Attach.md)|附加至 **VARIANT**`COleVariant`。|  
|[COleVariant::ChangeType](../Topic/COleVariant::ChangeType.md)|變更這 `COleVariant` 不同型別的物件。|  
|[COleVariant::Clear](../Topic/COleVariant::Clear.md)|清除這個 `COleVariant` 物件。|  
|[COleVariant::Detach](../Topic/COleVariant::Detach.md)|中斷連結 `COleVariant` 的 **VARIANT** 並傳回 **VARIANT**。|  
|[COleVariant::GetByteArrayFromVariantArray](../Topic/COleVariant::GetByteArrayFromVariantArray.md)|從現有的不同的陣列擷取位元組陣列。|  
|[COleVariant::SetString](../Topic/COleVariant::SetString.md)|將字串轉換為特定型別，通常為 ANSI。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[COleVariant::operator LPCVARIANT](../Topic/COleVariant::operator%20LPCVARIANT.md)|轉換 `COleVariant` 值至 `LPCVARIANT`。|  
|[COleVariant::operator LPVARIANT](../Topic/COleVariant::operator%20LPVARIANT.md)|轉換 `COleVariant` 物件。 `LPVARIANT`。|  
|[COleVariant::operator \=](../Topic/COleVariant::operator%20=.md)|複製 `COleVariant` 值。|  
|[COleVariant::operator \=\=](../Topic/COleVariant::operator%20==.md)|比較兩個 `COleVariant` 值。|  
|[COleVariant::operator \<\<, \>\>](../Topic/COleVariant::operator%20%3C%3C,%20%3E%3E.md)|輸出 `COleVariant` 值加入至 `CArchive` 或 `CDumpContext` 並輸入從 `CArchive`的 `COleVariant` 物件。|  
  
## 備註  
 這個資料型別用於 OLE Automation。  具體來說， [DISPPARAMS](http://msdn.microsoft.com/zh-tw/a16e5a21-766e-4287-b039-13429aa78f8b) 結構含有指向陣列 **VARIANT** 結構。  **DISPPARAMS** 結構用來傳遞參數至 [IDispatch::Invoke](http://msdn.microsoft.com/zh-tw/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
> [!NOTE]
>  這個類別會從 **VARIANT** 結構取得。  這表示您可以在 **VARIANT** 要求，並 **VARIANT** 結構的資料成員是 `COleVariant`的可存取的資料成員中的參數。 `COleVariant` 。  
  
 兩個關聯的 MFC 類別 [COleCurrency](../../mfc/reference/colecurrency-class.md) 和 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 封裝不同資料型別 **貨幣** \(`VT_CY`\) 和 **DATE** \(`VT_DATE`\)。  `COleVariant` 類別 DAO 類別會廣泛地使用;如需這個類別的一般使用方式，例如 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 和 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)參閱這些類別。  
  
 如需詳細資訊，請參閱 [Variant](http://msdn.microsoft.com/zh-tw/e305240e-9e11-4006-98cc-26f4932d2118)、 [貨幣](http://msdn.microsoft.com/zh-tw/5e81273c-7289-45c7-93c0-32c1553f708e)、 [DISPPARAMS](http://msdn.microsoft.com/zh-tw/a16e5a21-766e-4287-b039-13429aa78f8b)和 [IDispatch::Invoke](http://msdn.microsoft.com/zh-tw/964ade8e-9d8a-4d32-bd47-aa678912a54d) 輸入在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需 `COleVariant` 類別及其用法的詳細資訊在 OLE Automation，請參閱\<透過參數在 OLE Automation」本文 [自動化](../../mfc/automation.md)上。  
  
## 繼承階層架構  
 `tagVARIANT`  
  
 `COleVariant`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)