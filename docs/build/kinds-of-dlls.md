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

本主題提供的資訊可協助您判斷要建立的 DLL 類型。

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>可用的 Dll 種類不同

使用 Visual Studio，您可以在 C 或 c + + 中建立不使用 Microsoft Foundation Class （MFC）程式庫的 Win32 Dll。 您可以使用 Win32 應用程式精靈來建立非 MFC DLL 專案。

MFC 程式庫本身可以在靜態程式庫或數個 Dll 中使用，並搭配 MFC DLL Wizard。 如果您的 DLL 使用 MFC，Visual Studio 支援三種不同的 DLL 開發案例：

- 建立以靜態方式連結 MFC 的標準 MFC DLL

- 建立動態連結 MFC 的標準 MFC DLL

- 建立 MFC 延伸模組 DLL，其一律會以動態方式連結 MFC

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [非 MFC DLL：概觀](non-mfc-dlls-overview.md)

- [靜態連結至 MFC 的標準 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL：概觀](extension-dlls-overview.md)

- [要使用的 DLL 類型](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>決定要使用的 DLL 類型

如果您的 DLL 不使用 MFC，請使用 Visual Studio 來建立非 MFC 的 Win32 DLL。 將您的 DLL 連結至 MFC （靜態或動態）會佔用大量的磁碟空間和記憶體。 除非您的 DLL 實際使用 MFC，否則不應連結至 MFC。

如果您的 DLL 將使用 MFC，而 MFC 或非 MFC 應用程式會使用它，則您必須建立動態連結至 MFC 的標準 MFC DLL，或以靜態方式連結至 MFC 的一般 MFC DLL。 在大部分的情況下，您可能會想要使用動態連結至 MFC 的標準 MFC DLL，因為 DLL 的檔案大小會變得很小，而且使用共用版本的 MFC 所節省的記憶體可能會很重要。 如果您以靜態方式連結至 MFC，DLL 的檔案大小將會較大，而且可能會佔用額外的記憶體，因為它會載入自己的 MFC 程式庫程式碼私用複本。

建立動態連結至 MFC 的 DLL，會比建立以靜態方式連結至 MFC 的 DLL 更快速，因為不需要連結 MFC 本身。 這在連結器必須壓縮 debug 資訊的 debug 組建中特別適用。 藉由連結已包含偵錯工具資訊的 DLL，您的 DLL 內會有較少的偵錯工具資訊可精簡。

動態連結至 MFC 的一個缺點是，您必須使用 DLL 來散發共用 Dll Mfcx0 和 Msvcrxx （或類似檔案）。 MFC Dll 可自由轉散發，但您仍然必須在安裝程式中安裝 Dll。 此外，您還必須寄送 Msvcrxx，其中包含您的程式和 MFC Dll 本身所使用的 C 執行時間程式庫。

如果您的 DLL 只會由 MFC 可執行檔使用，您可以選擇建立一般 MFC DLL 或 MFC 擴充 DLL。 如果您的 DLL 會執行衍生自現有 MFC 類別的可重複使用類別，或您需要在應用程式和 DLL 之間傳遞 MFC 衍生物件，您必須建立 MFC 擴充 DLL。

如果您的 DLL 動態連結至 MFC，則 MFC Dll 可能會隨您的 DLL 一起轉散發。 此架構特別適合用來在多個可執行檔之間共用類別庫，以節省磁碟空間並將記憶體使用量降到最低。

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [非 MFC DLL：概觀](non-mfc-dlls-overview.md)

- [靜態連結至 MFC 的標準 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL：概觀](extension-dlls-overview.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
