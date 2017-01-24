---
title: "使用 CComBSTR 進行程式設計 (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComBSTR 類別, 程式設計"
  - "Unicode, 使用 CComBSTR [ATL]"
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CComBSTR 進行程式設計 (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 類別 [CComBSTR](../atl/reference/ccombstr-class.md) 在 `BSTR` 資料型別周圍的包裝函式。  當 `CComBSTR` 非常實用的工具時，不需要注意的數種情況。  
  
-   [轉換問題。](#programmingwithccombstr_conversionissues)  
  
-   [範圍問題](#programmingwithccombstr_scopeissues)  
  
-   [明確釋放 CComBSTR 物件](#programmingwithccombstr_explicitlyfreeing)  
  
-   [在迴圈中使用 CComBSTR 物件](#programmingwithccombstr_usingloops)  
  
-   [記憶體遺漏問題](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a> 轉換問題。  
 雖然許多 `CComBSTR` 方法會自動轉換成 ANSI 字串引數到 Unicode，方法永遠都會傳回 Unicode 格式字串。  若要轉換輸出至 ANSI 字串，請使用 ATL 轉換類別。  如需轉換 ATL 類別的詳細資訊，請參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
### 範例  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/CPP/programming-with-ccombstr-atl_1.cpp)]  
  
 如果您使用字串常值 \(String Literal\) `CComBSTR` 修改物件，請使用寬字元字串。  這會減少不必要的轉換。  
  
### 範例  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/CPP/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a> 範圍問題  
 會在超出範圍，以及任何行為良好的類別， `CComBSTR` 會釋放其資源。  如果函式傳回指向 `CComBSTR` 字串，這可能會造成問題，因為，指標會參考已經釋放的記憶體。  在這些情況下，請使用 **複本** 方法，如下所示。  
  
### 範例  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/CPP/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a> 明確釋放 CComBSTR 物件  
 在物件超出範圍之前，它可以是明確的可用 `CComBSTR` 物件包含的字串。  如果資料已釋放， `CComBSTR` 物件無效。  
  
### 範例  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/CPP/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a> 在迴圈中使用 CComBSTR 物件  
 因為 `CComBSTR` 類別配置緩衝區執行某些作業，例如 `+=` 運算子或 **附加** 方法，建議您不要執行在緊密迴圈內的字串管理。  在這些情況下， `CStringT` 提供更好的效能。  
  
### 範例  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/CPP/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a> 記憶體遺漏問題  
 傳遞初始化的 `CComBSTR` 的位址會當做參數 **\[out\]** 造成記憶體遺漏 \(Memory Leak\)。  
  
 在下列範例中，當函式 `MyGoodFunction` 取代字串時，配置的字串，會保留字串 `"Initialized"` 遺漏。  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/CPP/programming-with-ccombstr-atl_6.cpp)]  
  
 若要避免遺漏，請在傳遞這個位址之前呼叫在現有的 `CComBSTR` 物件的 **空** 方法做為 **\[out\]** 參數。  
  
 請注意相同的程式碼不會造成遺漏，如果函式的參數是 **\[in, out\]**。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../Topic/wstring.md)   
 [String Conversion Macros](../atl/reference/string-conversion-macros.md)