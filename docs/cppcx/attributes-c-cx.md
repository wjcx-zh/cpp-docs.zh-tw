---
title: "屬性 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# 屬性 (C++/CX)
屬性是 ref 類別的特殊類型，可括在方括弧中並附加至 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 類型和方法，以指定建立中繼資料時的特定行為。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 程式碼中通常會使用幾個預先定義的屬性，例如 [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx)。 此範例顯示如何將屬性套用至類別：  
  
 [!code-cpp[cx_attributes#01](../snippets/cpp/VS_Snippets_Misc/cx_attributes/cpp/class1.h#01)]  
  
## 自訂屬性  
 您也可以定義自訂屬性。 自訂屬性必須符合這些 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 規則：  
  
-   自訂屬性只能包含公用欄位。  
  
-   將屬性套用至類別之後，即可初始化自訂屬性欄位。  
  
-   欄位可以是下列其中一種類型：  
  
    -   int32 \(int\)  
  
    -   uint32 \(unsigned int\)  
  
    -   bool  
  
    -   Platform::String^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::Type^  
  
    -   公用列舉類別 \(包括使用者定義的列舉\)  
  
 下一個範例示範如何定義自訂屬性，然後在使用時予以初始化。  
  
 [!code-cpp[cx_attributes#02](../snippets/cpp/VS_Snippets_Misc/cx_attributes/cpp/class1.h#02)]  
  
## 請參閱  
 [類型系統 \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)