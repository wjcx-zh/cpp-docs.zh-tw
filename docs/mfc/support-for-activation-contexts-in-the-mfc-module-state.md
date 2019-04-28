---
title: MFC 模組狀態的啟用內容支援
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: a2e5f56eeb323f1bd5f20c5920bbdbe4a658554d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306661"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>MFC 模組狀態的啟用內容支援

MFC 會使用由使用者模組所提供的資訊清單資源來建立啟用內容。 如需如何建立啟用內容的詳細資訊，請參閱下列主題：

- [啟用內容](/windows/desktop/SbsCs/activation-contexts)

- [應用程式資訊清單](/windows/desktop/SbsCs/application-manifests)

- [組件資訊清單](/windows/desktop/SbsCs/assembly-manifests)

## <a name="remarks"></a>備註

當讀取這些 Windows SDK 主題，請注意不同之處在於 MFC 不會使用 Windows SDK 啟用內容 API MFC 啟用內容機制類似於 Windows SDK 的啟動內容。

透過下列方式在 MFC 應用程式、 使用者 Dll 和 MFC 擴充 Dll 可運作的啟動內容：

- MFC 應用程式會使用其資訊清單資源的資源 ID 1。 在這種情況下，MFC 不建立它的啟用內容，而是使用預設的應用程式內容。

- MFC 使用者 DLL 會使用它們的資訊清單資源的資源 ID 2。 在這裡，MFC 會為每個使用者 DLL 建立啟用內容，因此，不同的使用者 DLL 可以使用相同程式庫 (例如，通用控制項程式庫) 的不同版本。

- MFC 擴充 DLL 依賴其裝載應用程式或使用者 DLL 來建立它們的啟用內容。

雖然啟用內容狀態可以使用下所述的程序來修改[使用啟用內容 API](/windows/desktop/SbsCs/using-the-activation-context-api)，使用 MFC 啟用內容機制有助於進行開發 DLL 外掛程式結構並不容易 （或無法） 手動切換啟用狀態，在個別的呼叫外部外掛程式前後。

在中建立啟用內容[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)。 其會在 `AFX_MODULE_STATE` 解構函式被終結。 啟用內容控制代碼保留在 `AFX_MODULE_STATE` 中。 (`AFX_MODULE_STATE`所述[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)。)

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)巨集會啟用和停用啟用內容。 `AFX_MANAGE_STATE` 可針對 MFC 靜態程式庫及 MFC DLL 來啟用，如此便可讓 MFC 程式碼在使用者 DLL 選取的適當啟用內容中執行。

## <a name="see-also"></a>另請參閱

[啟用內容](/windows/desktop/SbsCs/activation-contexts)<br/>
[應用程式資訊清單](/windows/desktop/SbsCs/application-manifests)<br/>
[組件資訊清單](/windows/desktop/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
