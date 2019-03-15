---
title: DLL 的類型
ms.date: 11/04/2016
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: f4aa8b1be7cd9ad32b10f12c5d1dfd3ae86adc1d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820282"
---
# <a name="kinds-of-dlls"></a>DLL 的類型

本主題提供資訊以協助您決定要建置之 DLL 的種類。

##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> 不同類型的 Dll 可用

您可以使用 Visual c + +，建置以 C 或 c + + 的 Win32 Dll 不是使用 Microsoft Foundation Class (MFC) 程式庫。 您可以使用 Win32 應用程式精靈 建立非 MFC DLL 專案。

其中一個靜態連結程式庫中或在 Dll、 MFC DLL 精靈具有許多可用，MFC 程式庫本身。 如果您的 DLL 使用 MFC，Visual c + + 支援三種不同的 DLL 開發案例：

- 建置一般 MFC DLL 會以靜態方式連結至 MFC

- 建置一般 MFC DLL，以動態方式連結至 MFC

- 建置 MFC 擴充 DLL，這一律動態連結至 MFC

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [非 MFC DLL：概觀](non-mfc-dlls-overview.md)

- [靜態連結至 MFC 的標準 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL：概觀](extension-dlls-overview.md)

- [若要使用的 DLL 的種類](#_core_which_kind_of_dll_to_use)

##  <a name="_core_which_kind_of_dll_to_use"></a> 決定要使用的 DLL 的種類

如果您的 DLL 不使用 MFC，使用 Visual c + + 建置非 MFC Win32 DLL。 將您的 DLL 連結至 MFC （靜態或動態） 會佔用大量的磁碟空間和記憶體。 除非您的 DLL 實際上是使用 MFC，您不應該連結至 MFC。

如果您的 DLL 會使用 MFC，而且會由 MFC 或非 MFC 應用程式，您必須建置動態連結至 MFC 之標準 MFC DLL 或靜態連結至 MFC 之標準 MFC DLL。 在大部分情況下，您可能想要使用動態連結至 MFC，因為 DLL 的檔案大小會小很多，而且在使用 MFC 的共用的版本的記憶體中的節省金額可能會顯著的標準 MFC DLL。 如果您以靜態方式連結至 MFC，您的 DLL 的檔案大小會大很多，並可能佔用額外的記憶體，因為它會載入自己的 MFC 程式庫程式碼的私用複本。

建置動態連結至 MFC 的 DLL 的速度會比建置靜態連結至 MFC，因為它不需要連結 MFC 本身的 DLL。 特別是在偵錯組建，連結器必須壓縮偵錯資訊。 藉由連結與已經包含偵錯資訊的 DLL，沒有較少至精簡您的 DLL 內的偵錯資訊。

動態連結至 MFC 的一個缺點是，您必須將共用的 Dll Mfcx0.dll 和 Msvcrxx.dll （或類似檔案） 與您的 DLL。 MFC Dll 可以自由轉散發，但您仍然必須安裝 Dll 中您的安裝程式。 此外，您必須將 Msvcrxx.dll，它包含會使用您的程式和 MFC Dll 本身的 C 執行階段程式庫。

如果您的 DLL 只會由 MFC 可執行檔，您可以選擇建置標準的 MFC DLL 或 MFC 擴充 DLL。 如果您的 DLL 實作衍生自現有 MFC 類別的可重複使用類別或您需要應用程式和 DLL 之間傳遞 MFC 衍生的物件，您必須建置 MFC 擴充 DLL。

如果您的 DLL 動態連結至 MFC，可能會與您的 DLL 轉散發 MFC Dll。 此架構是特別適用於共用類別庫，以節省磁碟空間和記憶體使用量降到最低的多個可執行檔之間。

之前的版本 4.0，Visual c + + 只支援兩種使用 MFC 的 Dll:Usrdll 和 Afxdll。 靜態連結至 MFC 的標準 MFC Dll 有相同的特性，與之前的 usrdll。 MFC 擴充 Dll 有相同的特性，與之前的 Afxdll。

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [非 MFC DLL：概觀](non-mfc-dlls-overview.md)

- [靜態連結至 MFC 的標準 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [動態連結至 MFC 的標準 MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 延伸模組 DLL：概觀](extension-dlls-overview.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
