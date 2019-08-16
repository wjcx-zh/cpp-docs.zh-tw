---
title: MFC 模組狀態的啟用內容支援
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: 296df3d2ecec74c5c9a7deef1617298d40243724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511428"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>MFC 模組狀態的啟用內容支援

MFC 會使用由使用者模組所提供的資訊清單資源來建立啟用內容。 如需如何建立啟用內容的詳細資訊，請參閱下列主題：

- [啟用內容](/windows/win32/SbsCs/activation-contexts)

- [應用程式資訊清單](/windows/win32/SbsCs/application-manifests)

- [組件資訊清單](/windows/win32/SbsCs/assembly-manifests)

## <a name="remarks"></a>備註

閱讀這些 Windows SDK 主題時, 請注意 MFC 啟用內容機制類似于 Windows SDK 啟用內容, 不同之處在于 MFC 不會使用 Windows SDK 啟用內容 API。

啟用內容會以下列方式在 MFC 應用程式、使用者 Dll 和 MFC 擴充 Dll 中運作:

- MFC 應用程式會使用其資訊清單資源的資源 ID 1。 在這種情況下，MFC 不建立它的啟用內容，而是使用預設的應用程式內容。

- MFC 使用者 DLL 會使用它們的資訊清單資源的資源 ID 2。 在這裡，MFC 會為每個使用者 DLL 建立啟用內容，因此，不同的使用者 DLL 可以使用相同程式庫 (例如，通用控制項程式庫) 的不同版本。

- MFC 擴充 DLL 依賴其裝載應用程式或使用者 DLL 來建立它們的啟用內容。

雖然啟用內容狀態可使用[使用啟用內容 API](/windows/win32/SbsCs/using-the-activation-context-api)底下所述的程式進行修改, 但使用 MFC 啟用內容機制在開發 DLL 型外掛程式架構時可能會很有用 (或不可能) 在個別呼叫外部外掛程式之前和之後手動切換啟用狀態。

啟用內容是在[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)中建立的。 其會在 `AFX_MODULE_STATE` 解構函式被終結。 啟用內容控制代碼保留在 `AFX_MODULE_STATE` 中。 (`AFX_MODULE_STATE`如[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)所述)。

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)宏會啟用和停用啟用內容。 `AFX_MANAGE_STATE` 可針對 MFC 靜態程式庫及 MFC DLL 來啟用，如此便可讓 MFC 程式碼在使用者 DLL 選取的適當啟用內容中執行。

## <a name="see-also"></a>另請參閱

[啟用內容](/windows/win32/SbsCs/activation-contexts)<br/>
[應用程式資訊清單](/windows/win32/SbsCs/application-manifests)<br/>
[組件資訊清單](/windows/win32/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
