---
title: "如何： 直接執行個體化 WRL 元件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2d307304c103b62ff5ba20e1af25797745bd035
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-instantiate-wrl-components-directly"></a>如何：直接執行個體化 WRL 元件
了解如何使用 Windows 執行階段 c + + 樣板程式庫 (WRL)[Microsoft::WRL::Make](../windows/make-function.md)和[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)函式來具現化元件，以從模組，定義它。  
  
 藉由直接執行個體化元件，您可以減少額外負荷時，不需要 class factory 或其他機制。 您可以直接在兩個通用 Windows 平台應用程式和桌面應用程式中的元件具現化。  
  
 若要深入了解如何使用 Windows 執行階段 c + + 樣板程式庫來建立基本 Windows 執行階段元件和外部的通用 Windows 平台應用程式具現化，請參閱[逐步解說： 建立基本 Windows 執行階段元件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)。 若要深入了解如何使用 Windows 執行階段 c + + 樣板程式庫建立傳統 COM 元件，並從外部的桌面應用程式具現化，請參閱[How to： 建立傳統 COM 元件](../windows/how-to-create-a-classic-com-component-using-wrl.md)。  
  
 這份文件會顯示兩個範例。 第一個範例會使用`Make`函式來具現化元件。 第二個範例會使用`MakeAndInitialize`函式來具現化可能會在建構期間失敗的元件。 (因為通常會使用 COM`HRESULT`值，而不是例外狀況，來指出錯誤，COM 型別通常不會擲回從其建構函式。 `MakeAndInitialize`可讓元件以驗證其建構引數到`RuntimeClassInitialize`方法。)這兩個範例會定義基本記錄器介面，並藉由定義將訊息寫入主控台的類別中實作該介面。  
  
> [!IMPORTANT]
>  您無法使用`new`運算子來具現化的 Windows 執行階段 c + + 樣板程式庫元件。 因此，我們建議一律使用`Make`或`MakeAndInitialize`來具現化元件直接。  
  
### <a name="to-create-and-instantiate-a-basic-logger-component"></a>建立及具現化基本記錄器元件  
  
1.  在 Visual Studio 中建立**Win32 主控台應用程式**專案。 為專案命名，例如`WRLLogger`。  
  
2.  新增**Midl 檔 (.idl)**檔案加入專案中，將檔案命名`ILogger.idl`，然後新增此程式碼：  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  您可以使用下列程式碼取代 WRLLogger.cpp 的內容。  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>若要處理基本記錄器元件的建構失敗  
  
1.  使用下列程式碼的定義取代`CConsoleWriter`類別。 這個版本會保留私用 string 成員變數和覆寫`RuntimeClass::RuntimeClassInitialize`方法。 `RuntimeClassInitialize`如果失敗的呼叫`SHStrDup`失敗。  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  使用下列程式碼的定義取代`wmain`。 此版本使用`MakeAndInitialize`來具現化`CConsoleWriter`物件並檢查`HRESULT`結果。  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)