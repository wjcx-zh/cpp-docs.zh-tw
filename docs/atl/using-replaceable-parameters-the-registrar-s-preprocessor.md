---
title: "Using Replaceable Parameters (The Registrar&#39;s Preprocessor) | Microsoft Docs"
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
  - "AddReplacement"
  - "ClearReplacements"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%MODULE%"
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using Replaceable Parameters (The Registrar&#39;s Preprocessor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可取代的參數可讓管理員的用戶端指定執行階段資料。  若要這樣做，管理員會維護其輸入值與在指令碼中可取代參數的取代對應。  管理員對這些項目在執行階段。  
  
##  <a name="_atl_using_.25.module.25"></a> 使用 %MODULE%  
 [ATL 控制項精靈](../atl/reference/atl-control-wizard.md) 自動產生使用 `%MODULE%`的指令碼。  ATL 對伺服器的 DLL 或 EXE 的實際位置使用這可取代的參數。  
  
## 串連指令碼資料的執行階段資料  
 對前置處理器的另一個用途是串連指令碼資料的執行階段資料。  例如，假設輸入需要包含完整路徑具有字串「`, 1`」的模組已附加至這個結尾。  首先，請定義下列副檔名:  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 然後，在呼叫處理方法的上一個指令碼列出 [叫用指令碼](../atl/invoking-scripts.md)，請將取代為要對應:  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/CPP/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 在剖析期間，指令碼管理員展開 `'%MODULE%, 1'` 至 `c:\mycode\mydll.dll, 1`。  
  
> [!NOTE]
>  在登錄器指令碼， 4K 最大語彙基元大小。  \(語彙基元是語法的任何可辨識的項目\)。這包括由前置處理器建立或擴充的語彙基元。  
  
> [!NOTE]
>  若要以取代的值在執行階段，請移除指令碼的呼叫 [DECLARE\_REGISTRY\_RESOURCE](../Topic/DECLARE_REGISTRY_RESOURCE.md) 或 [DECLARE\_REGISTRY\_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md) 巨集。  相反地，請透過呼叫 [CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md) 或 [CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md)的 `UpdateRegistry` 方法取代它，並將陣列 **\_ATL\_REGMAP\_ENTRY** 結構。  您的陣列 **\_ATL\_REGMAP\_ENTRY** 必須設定至少一個輸入**NULL**{，}，**NULL**，而且此項目必須是最後一個項目。  否則，當呼叫， **UpdateRegistryFromResource** 存取違規，則會產生錯誤。  
  
> [!NOTE]
>  在建立專案時的輸出可執行檔， ATL 在路徑名稱自動在別名前後加入引號建立在與 **%MODULE%** 登錄器指令碼參數的執行階段。  如果您不希望路徑名稱中包含引號，請使用新的 **%MODULE\_RAW%** 參數。  
>   
>  在建立專案時輸出 DLL， ATL 不會將引號加入路徑名稱，如果使用 **%MODULE%** 或 **%MODULE\_RAW%** 。  
  
## 請參閱  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)