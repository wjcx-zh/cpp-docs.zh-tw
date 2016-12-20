---
title: "如何：直接執行個體化 WRL 元件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：直接執行個體化 WRL 元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

了解如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)]\([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\)[Microsoft::WRL::Make](../windows/make-function.md)和[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)這兩隻函式，從定義元件的模組中具現化元件。  
  
 您可以直接具現化元件，在您不需要 Class Factory 或其他機制時來減少額外負荷。  您可以在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式與傳統型應用程式中直接具現化元件。  
  
 若要了解如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 建立基本 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件，以及從外部 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式具現化，請參閱 [逐步解說：建立基本 Windows 執行階段元件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)。  若要了解如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 建立典型COM 元件，以及從外部傳統型應用程式具現化，請參閱 [如何：建立傳統 COM 元件](../windows/how-to-create-a-classic-com-component-using-wrl.md) 。  
  
 這個文件顯示兩個範例。  第一個範例會使用 `Make` 函式產生元件。  第二個範例會使用 `MakeAndInitialize` 函式具現化在建構期間可能會失敗的元件。\(由於 COM 一般會使用 `HRESULT` 值取代例外狀況來表示錯誤， COM 型別通常不會從它的建構函式擲回。  `MakeAndInitialize` 可讓元件透過 `RuntimeClassInitialize` 方法驗證其建構函式引數\)。以上兩個範例皆會定義基本記錄器介面，並藉由定義會寫入訊息至主控台的類別實作該介面。  
  
> [!IMPORTANT]
>  您不能使用 `new` 運算子執行個體化 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 元件。  因此，建議您一律使用 `Make` 或 `MakeAndInitialize` 直接產生元件。  
  
### 建立及初始化基本記錄器元件  
  
1.  在 Visual Studio 中建立**Win32 主控台應用程式**專案。  命名專案，例如`WRLLogger`。  
  
2.  將 \[**Midl 檔案 \(.idl\)**\] 檔案加到專案，並將檔案命名為 `ILogger.idl`，然後將下列程式碼：  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  以下列程式碼取代 WRLLogger.cpp 的內容：  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### 處理基本記錄器元件的建構失敗  
  
1.  以下列程式碼取代 `CConsoleWriter` 類別的定義。  此版本保留私用字串成員變數並覆寫 `RuntimeClass::RuntimeClassInitialize` 方法。  如果對 `SHStrDup` 的呼叫失敗，`RuntimeClassInitialize` 會失敗。  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  將 `wmain` 的定義替換成下列程式碼。  這個版本使用 `MakeAndInitialize` 具現化 `CConsoleWriter` 物件並檢查 `HRESULT` 結果。  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## 請參閱  
 [Windows Runtime C\+\+ Template Library \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)