---
title: ATL 精靈加入 ATL 支援的詳細資訊
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 0b849ffb585ef99512cc68e1c734dc5b3a87d507
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304921"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 精靈加入 ATL 支援的詳細資訊

當您[將 ATL 支援加入至現有的 MFC 可執行檔或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)，Visual c + + 可讓下列修改現有的 MFC 專案 (在此範例中的專案稱為`MFCEXE`):

- 會新增兩個新的檔案 （.idl 檔和.rgs 檔案，用來註冊的伺服器）。

- 在主應用程式標頭和實作檔案 （Mfcexe.h 和 Mfcexe.cpp），新的類別 (衍生自`CAtlMFCModule`) 加入。 除了新的類別，程式碼加入至`InitInstance`進行註冊。 程式碼也會加入至`ExitInstance`撤銷類別物件的函式。 在標頭檔中，最後，兩個新標頭檔 （h 和 Mfcexe_i.c） 包含在實作檔案中，宣告並初始化新的 Guid，如`CAtlMFCModule`-衍生的類別。

- 若要正確地註冊伺服器，新的.rgs 檔案的項目會新增至專案的資源檔案。

## <a name="notes-for-dll-projects"></a>DLL 專案的相關資訊

當您將 ATL 支援加入 MFC DLL 專案時，您會看到一些差異。 程式碼加入至`DLLRegisterServer`和`DLLUnregisterServer`註冊和取消註冊 DLL 的函式。 程式碼也會加入至[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)並[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)。

## <a name="see-also"></a>另請參閱

[MFC 專案中的 ATL 支援](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
