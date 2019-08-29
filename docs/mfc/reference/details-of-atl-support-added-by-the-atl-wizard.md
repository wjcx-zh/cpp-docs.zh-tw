---
title: ATL 精靈加入 ATL 支援的詳細資訊
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 10bafc9bd06ee94398f91d5af478a6e1cd7ca617
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108446"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 精靈加入 ATL 支援的詳細資訊

::: moniker range=">=vs-2019"

當您[將 ATL 支援新增至現有的 MFC 可執行檔或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)時, Visual Studio 預設會加入名為*framework .h*的頭`#include`檔`#define` , 其中包含和預處理器指示詞, 可讓您在專案中使用 ATL。 不會新增任何其他檔案或類別, 就像舊版的 Visual Studio 中所做的一樣。

::: moniker-end

::: moniker range="<=vs-2017"

當您[將 ATL 支援加入至現有的 mfc 可執行檔或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)時, Visual Studio 會對現有的 mfc 專案進行下列修改 (在此範例中`MFCEXE`, 會呼叫專案):

- 新增兩個新檔案 (.idl 檔案和用來註冊伺服器的 .rgs 檔案)。

- 在主要應用程式標頭和執行檔案 (Mfcexe .h 和 Mfcexe) 中, 會加入新的類別 (衍生`CAtlMFCModule`自)。 除了新的類別之外, 也會將程式碼`InitInstance`新增至以進行註冊。 程式碼也會新增至`ExitInstance`函式, 以撤銷類別物件。 在標頭檔中, 最後會有兩個新的標頭檔 (d 和 Mfcexe_i) 包含在執行檔中, 宣告和初始化衍生類別的新 guid `CAtlMFCModule`。

- 為了正確註冊伺服器, 新的 .rgs 檔案的專案會新增至專案的資源檔。

::: moniker-end

## <a name="notes-for-dll-projects"></a>DLL 專案的注意事項

當您將 ATL 支援新增至 MFC DLL 專案時, 您會看到一些差異。 程式碼會新增至`DLLRegisterServer`和`DLLUnregisterServer`函式, 以供註冊及取消註冊 DLL。 程式碼也會新增至[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)和[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)。

## <a name="see-also"></a>另請參閱

[MFC 專案中的 ATL 支援](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigate-code-cpp.md)
