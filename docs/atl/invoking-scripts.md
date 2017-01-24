---
title: "Invoking Scripts | Microsoft Docs"
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
  - "StringRegister"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "指令碼, invoking registry in ATL"
  - "StringRegister method"
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Invoking Scripts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[使用可取代的參數 \(管理員的前置處理器\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 討論取代對應和提到管理員方法 **AddReplacement**。  管理員對其他八方法特有的指令碼，然後，所有在下表中說明。  
  
|方法|語法與描述|  
|--------|-----------|  
|**ResourceRegister**|**HRESULT ResourceRegister\( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType`\);<br /><br /> 登錄記錄在模組的資源中的指令碼。  表示*resFileName* UNC 路徑加入至模組。  `nID` 和 `szType` 包含資源的 ID 和型別，分別。|  
|**ResourceUnregister**|**HRESULT ResourceUnregister\( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType`\);<br /><br /> 移除註冊所在模組的資源中的指令碼。  表示*resFileName* UNC 路徑加入至模組。  `nID` 和 `szType` 包含資源的 ID 和型別，分別。|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz\( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType`\);<br /><br /> 登錄記錄在模組的資源中的指令碼。  表示*resFileName* UNC 路徑加入至模組。  *szID* 和 `szType` 包含資源的字串識別項和型別，分別。|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz\( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType`\);<br /><br /> 移除註冊所在模組的資源中的指令碼。  表示*resFileName* UNC 路徑加入至模組。  *szID* 和 `szType` 包含資源的字串識別項和型別，分別。|  
|**FileRegister**|**HRESULT FileRegister\( LPCOLESTR**  *檔名* \);<br /><br /> 登錄檔案中的指令碼。  *filename* 是 UNC 路徑加入至包含的檔案 \(或\) 是一個資源指令碼。|  
|**FileUnregister**|**HRESULT FileUnregister\( LPCOLESTR**  *檔名* \);<br /><br /> 移除檔案中的指令碼。  *filename* 是 UNC 路徑加入至包含的檔案 \(或\) 是一個資源指令碼。|  
|**StringRegister**|**HRESULT StringRegister\( LPCOLESTR**  *資料* \);<br /><br /> 登錄中的指令碼。  資料包含指令碼。|  
|**StringUnregister**|**HRESULT StringUnregister\( LPCOLESTR**  *資料* \);<br /><br /> 將字串中的指令碼。  資料包含指令碼。|  
  
 **ResourceRegisterSz** 和 **ResourceUnregisterSz**，類似於 **ResourceRegister** 和 **ResourceUnregister**，不過，可讓您指定字串識別項。  
  
 方法 **FileRegister** 和 **FileUnregister** 很有用，如果您不想在資源指令碼，或者如果您想要在自己的檔案中的指令碼。  方法 **StringRegister** 和 **StringUnregister** 在動態配置的字串允許 .rgs 檔案中。  
  
## 請參閱  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)