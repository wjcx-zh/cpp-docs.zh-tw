---
title: "Dll 的種類 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47ce4a9264a59f88f22cd40bc3b6d6620c9702c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="kinds-of-dlls"></a>DLL 的類型
本主題提供資訊以協助您決定要建置的 DLL 的種類。  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>不同類型的 Dll 可用  
 使用 Visual c + +，您可以建置在 C 或 c + + 中的 Win32 Dll 不是使用 Microsoft Foundation Class (MFC) 程式庫。 您可以使用 Win32 應用程式精靈建立的非 MFC DLL 專案。  
  
 數字的 Dll，以 MFC DLL 精靈或其中一個靜態連結程式庫中使用，在 MFC 程式庫本身。 如果您的 DLL 會使用 MFC，Visual c + + 支援三種不同的 DLL 開發案例：  
  
-   建置一般 MFC 的 DLL，以靜態方式連結 MFC  
  
-   建置一般 MFC 的 DLL，以動態方式連結 MFC  
  
-   建置 MFC 擴充 DLL，這一律動態連結至 MFC  
  
### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)  
  
-   [以靜態方式連結至 MFC 的標準 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 延伸模組 DLL：概觀](../build/extension-dlls-overview.md)  
  
-   [若要使用的 DLL 的種類](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a>決定要使用的 DLL 的種類  
 如果您的 DLL 不使用 MFC，使用 Visual c + + 來建立非 MFC Win32 DLL。 （靜態或動態） 連結至 MFC 的 DLL 會佔用大量的磁碟空間和記憶體。 除非您的 DLL 實際上會使用 MFC，您不應該連結至 MFC。  
  
 如果您的 DLL 將會使用 MFC，而且將供 MFC 或非 MFC 應用程式，您必須建置動態連結至 MFC 之標準 MFC DLL 或靜態連結至 MFC 之標準 MFC DLL。 在大部分情況下，您可能想要使用，因為 DLL 的檔案大小會小很多，節省的記憶體使用 MFC 的共用的版本可能會很顯著，動態連結至 MFC 的標準 MFC DLL。 如果您以靜態方式連結至 MFC，DLL 的檔案大小將會變大，並可能佔用額外的記憶體，因為它會載入它自己的 MFC 程式庫程式碼的私用複本。  
  
 建置動態連結至 MFC 的 DLL 會比建置的 DLL，因為它不需要連結 MFC 靜態連結至 MFC 更快。 特別是在連結器必須在其中壓縮的偵錯資訊的偵錯組建。 連結的 DLL，已包含偵錯資訊，偵錯資訊變少了壓縮 DLL 中。  
  
 動態連結至 MFC 的一個缺點是您必須使用您的 DLL 發佈共用的 Dll Mfcx0.dll Msvcrxx.dll （或類似檔案）。 MFC Dll 可以自由轉，但您仍然必須安裝 Dll，安裝程式中。 此外，您必須提供 Msvcrxx.dll，其中包含您的程式和 MFC Dll 本身都能使用 C 執行階段程式庫。  
  
 如果您的 DLL 只會由 MFC 可執行檔，您可以選擇建置標準的 MFC DLL 或 MFC 擴充 DLL。 如果您的 DLL 會實作衍生自現有 MFC 類別的可重複使用類別或您需要將應用程式和 DLL 之間的 MFC 衍生物件，您必須建置 MFC 擴充 DLL。  
  
 如果您的 DLL 動態連結至 MFC，可能會與您的 DLL 轉散發 MFC Dll。 此架構是特別適用於共用來節省磁碟空間及記憶體使用量降到最低的多個可執行檔之間的類別庫。  
  
 之前的版本 4.0 中，Visual c + + 只支援兩種使用 MFC 的 Dll: USRDLLs 和 AFXDLLs。 以靜態方式連結至 MFC 的標準 MFC Dll 具有先前 USRDLL 相同的特性。 MFC 擴充 Dll 中有先前 AFXDLLs 相同的特性。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)  
  
-   [以靜態方式連結至 MFC 的標準 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 延伸模組 DLL：概觀](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)