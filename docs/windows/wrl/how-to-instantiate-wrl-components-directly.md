---
title: HOW TO：直接執行個體化 WRL 元件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: 3caa29125de0de8cbe73379b8d7244206a5f9229
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336170"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>HOW TO：直接執行個體化 WRL 元件

了解如何使用 Windows 執行階段 c + + 範本庫 (WRL)[Microsoft::WRL::Make](make-function.md)並[Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)函式來具現化元件，以從模組，其定義。

藉由直接執行個體化的元件，您可以減少額外負荷時，不需要 class factory 或其他機制。 您可以直接在兩個通用 Windows 平台應用程式和桌面應用程式中的元件具現化。

若要了解如何使用 Windows 執行階段 c + + 樣板程式庫建立傳統 COM 元件，並加以具現化從外部的傳統型應用程式，請參閱[How to:建立傳統 COM 元件](how-to-create-a-classic-com-component-using-wrl.md)。

本文件說明兩個範例。 第一個範例會使用`Make`函式來具現化元件。 第二個範例會使用`MakeAndInitialize`函式來具現化可能會在建構期間失敗的元件。 （由於 COM 通常會使用而不是例外狀況的 HRESULT 值，來指出錯誤，COM 型別通常不會擲回從其建構函式。 `MakeAndInitialize` 啟用元件，驗證透過其建構引數`RuntimeClassInitialize`方法。)這兩個範例會定義基本的記錄器的介面，並實作該介面所定義的類別，將訊息寫入主控台。

> [!IMPORTANT]
> 您無法使用`new`運算子來具現化 Windows 執行階段 c + + 樣板程式庫元件。 因此，我們建議您一律使用`Make`或`MakeAndInitialize`來具現化元件直接。

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>若要建立並具現化基本記錄器元件

1. 在 Visual Studio 中建立**Win32 主控台應用程式**專案。 為專案命名，例如*WRLLogger*。

2. 新增**Midl 檔 (.idl)** 檔案加入專案中，將檔案命名為`ILogger.idl`，然後新增此程式碼：

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. 使用下列程式碼的內容取代`WRLLogger.cpp`。

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>若要處理建構基本記錄器元件失敗

1. 使用下列的程式碼取代定義`CConsoleWriter`類別。 這個版本會保留私用字串成員變數，並覆寫`RuntimeClass::RuntimeClassInitialize`方法。 `RuntimeClassInitialize` 如果失敗的呼叫`SHStrDup`失敗。

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. 使用下列的程式碼取代定義`wmain`。 此版本會使用`MakeAndInitialize`具現化`CConsoleWriter`物件，並檢查 HRESULT 結果。

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft::WRL::Make](make-function.md)<br/>
[Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)