---
title: DLL 的類型
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: dae44d2dd39597420ce2a2c4e1642e8a7f0784e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328506"
---
# <a name="kinds-of-dlls"></a>DLL 的類型

本主題提供的資訊可説明您確定要構建的 DLL 類型。

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>提供不同類型的 DLL

使用 Visual Studio,您可以在 C 或不使用 Microsoft 基礎類 (MFC) 庫的 C++中構建 Win32 DLL。 您可以使用 Win32 應用程式精靈建立非 MFC DLL 專案。

MFC 庫本身在靜態連結庫中或多個 DLL 中可用,帶有 MFC DLL 嚮導。 如果您的 DLL 使用 MFC,Visual Studio 支援三種不同的 DLL 開發方案:

- 建構一個常規的 MFC DLL,以靜態方式連結 MFC

- 建構動態連結 MFC 的一般 MFC DLL

- 建構 MFC 延伸 DLL,始終動態連結 MFC

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [非 MFC DLL：概觀](non-mfc-dlls-overview.md)

- [一般 MFC DLL 靜態連結到 MFC](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL：概觀](extension-dlls-overview.md)

- [使用哪種 DLL](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>決定使用哪種 DLL

如果您的 DLL 不使用 MFC,請使用 Visual Studio 構建非 MFC Win32 DLL。 將 DLL 連結到 MFC(靜態或動態)會佔用大量磁碟空間和記憶體。 除非 DLL 實際使用 MFC,否則不應連結到 MFC。

如果您的 DLL 將使用 MFC,並且將由 MFC 或非 MFC 應用程式使用,則必須建構動態連結到 MFC 的常規 MFC DLL 或靜態連結到 MFC 的一般 MFC DLL。 在大多數情況下,您可能需要使用動態連結到 MFC 的常規 MFC DLL,因為 DLL 的檔大小將小得多,並且使用 MFC 的共用版本可以節省記憶體。 如果靜態連結到 MFC,則 DLL 的檔大小將更大,並可能佔用額外的記憶體,因為它載入了 MFC 庫代碼的私有副本。

構建動態連結到 MFC 的 DLL 比建構一個靜態連結到 MFC 的 DLL 更快,因為沒有必要連結 MFC 本身。 在調試生成中尤其如此,其中連結器必須壓縮調試資訊。 通過連結到已包含調試資訊的 DLL,DLL 中要壓縮的調試資訊就更少了。

動態連結到 MFC 的一個缺點是,您必須將共用的 DlL Mfcx0.dll 和 Msvcrxx.dll(或類似檔)與 DLL 一起分發。 MFC DLL 可自由再分發,但您仍必須在安裝程式中安裝 DLL。 此外,您必須提供 Msvcrxx.dll,其中包含程式和 MFC DLL 本身使用的 C 執行時庫。

如果 DLL 僅由 MFC 可執行檔使用,則可以在構建常規 MFC DLL 或 MFC 擴展 DLL 之間進行選擇。 如果 DLL 實現了從現有 MFC 類派生的可重用類,或者需要在應用程式和 DLL 之間傳遞 MFC 派生的物件,則必須構建 MFC 擴展 DLL。

如果您的 DLL 動態連結到 MFC,則 MFC DLL 可能會與您的 DLL 重新分發。 此體系結構對於在多個可執行文件之間共用類庫以節省磁碟空間並最大限度地減少記憶體使用量特別有用。

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [非 MFC DLL：概觀](non-mfc-dlls-overview.md)

- [一般 MFC DLL 靜態連結到 MFC](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL：概觀](extension-dlls-overview.md)

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
