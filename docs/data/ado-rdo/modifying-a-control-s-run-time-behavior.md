---
title: "修改控制項的執行階段行為 | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 執行階段行為"
ms.assetid: 78b44b0f-0d5a-4da0-8aa2-595f5789c634
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 修改控制項的執行階段行為
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您[插入控制項](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)並產生一或多個[包裝函式類別](../../data/ado-rdo/wrapper-classes.md)之後，可叫用控制項的方法，並為控制項的事件處理常式設計程式。  
  
 控制項的[包裝函式類別](../../data/ado-rdo/wrapper-classes.md)指定了可用來修改控制項執行階段行為的函式。 請包含適當的包裝函式類別標頭檔，並使用其方法。 若要設定屬性，請尋找屬性名稱前面加上 Set 的存取子方法。 若要擷取屬性，請尋找屬性名稱前面加上 Get 的存取子方法。 稍後可以撰寫事件處理常式。  
  
 由於控制項是透過自動化來實作，因此傳遞的類型只能是自動化安全類型，例如 BSTR 和 VARIANT。 雖然您可以使用系統呼叫來配置及設定 BSTR 和 VARIANT，您可能會想要使用 ATL 包裝函式類別 \([CComBSTR](../../atl/reference/ccombstr-class.md)、[CComVariant](../../atl/reference/ccomvariant-class.md)\)、Visual C\+\+ COM 編譯器支援的包裝函式類別 \([\_bstr\_t](../../cpp/bstr-t-class.md)、[\_variant\_t](../../cpp/variant-t-class.md)\) 或 MFC 包裝函式類別 \([COleVariant](../../mfc/reference/colevariant-class.md)\)。  
  
 如果您加入資料控制項，\[插入 ActiveX 控制項精靈\] 會為該資料控制項的 CoClasses 產生包裝函式類別，以管理其內部資料物件。 這些類別並未包含所有 RDO 或 ADO，而只是代表在類型程式庫中宣告的內部物件。  
  
 如果您想要直接使用 ADO 和 RDO，則應該透過[編譯器 COM 支援類別](../../cpp/compiler-com-support-classes.md) \(支援 [\#import 指示詞](../../preprocessor/preprocessor-directives.md)\) 或個別 SDK，直接連接到 ADO 或 RDO DLL \(Msado15.dll 或 Msrdo20.dll\)。  
  
## 在執行階段設定控制項屬性  
 請注意，ActiveX 控制項的某些屬性在執行階段可能是唯讀的，因此很難動態建立。 您可以如知識庫文章：＜如何：在執行階段設定 ActiveX 控制項設計階段屬性 \(Q260744\)＞中所述，透過覆寫控制項容器的 [OnAmbientPropertyChange](../Topic/COleControl::OnAmbientPropertyChange.md) 處理常式來暫時模擬設計模式，以進行屬性初始化作業。 您可以在 [http:\/\/support.microsoft.com\/](http://support.microsoft.com/) 找到知識庫文章。  
  
## 請參閱  
 [使用 ActiveX 控制項](../../data/ado-rdo/using-activex-controls.md)