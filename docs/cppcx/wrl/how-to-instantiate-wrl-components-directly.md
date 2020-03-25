---
title: 如何：直接執行個體化 WRL 元件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: f291e982d7f77c63821e5943a5867662ccd1b4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213898"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>如何：直接執行個體化 WRL 元件

瞭解如何使用 Windows 執行階段C++範本庫（WRL）[MICROSOFT：： WRL：： Make](make-function.md)和[microsoft：： WRL：:D etails：： MakeAndInitialize](makeandinitialize-function.md)函式，從定義元件的模組中具現化元件。

藉由直接具現化元件，當您不需要 class factory 或其他機制時，可以減少額外負荷。 您可以直接在通用 Windows 平臺應用程式和桌面應用程式中具現化元件。

若要瞭解如何使用 Windows 執行階段C++範本程式庫來建立傳統的 com 元件，並從外部桌面應用程式將它具現化，請參閱[如何：建立傳統 com 元件](how-to-create-a-classic-com-component-using-wrl.md)。

本檔說明兩個範例。 第一個範例使用 `Make` 函數來具現化元件。 第二個範例會使用 `MakeAndInitialize` 函式來具現化可能在結構中失敗的元件。 （由於 COM 通常會使用 HRESULT 值，而不是例外狀況來表示錯誤，因此 COM 類型通常不會從其函式中擲回。 `MakeAndInitialize` 可讓元件透過 `RuntimeClassInitialize` 方法來驗證其結構引數）。這兩個範例都會定義一個基本記錄器介面，並藉由定義將訊息寫入主控台的類別來實作為介面。

> [!IMPORTANT]
> 您無法使用 `new` 運算子來具現化C++ Windows 執行階段的範本程式庫元件。 因此，我們建議您一律使用 `Make` 或 `MakeAndInitialize`，直接將元件具現化。

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>建立和具現化基本記錄器元件

1. 在 Visual Studio 中，建立**Win32 主控台應用程式**專案。 為專案命名，例如*WRLLogger*。

2. 將**Midl 檔案（.idl）** 檔案新增至專案，將檔案命名為 `ILogger.idl`，然後新增下列程式碼：

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. 使用下列程式碼來取代 `WRLLogger.cpp`的內容。

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>若要處理基本記錄器元件的結構失敗

1. 使用下列程式碼來取代 `CConsoleWriter` 類別的定義。 這個版本會保存私用字串成員變數，並覆寫 `RuntimeClass::RuntimeClassInitialize` 方法。 如果呼叫 `SHStrDup` 失敗，`RuntimeClassInitialize` 會失敗。

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. 使用下列程式碼來取代 `wmain`的定義。 這個版本會使用 `MakeAndInitialize` 來具現化 `CConsoleWriter` 物件，並檢查 HRESULT 結果。

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft：： WRL：： Make](make-function.md)<br/>
[Microsoft：： WRL：:D etails：： MakeAndInitialize](makeandinitialize-function.md)
