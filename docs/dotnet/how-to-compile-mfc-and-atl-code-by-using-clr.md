---
title: HOW TO：使用-clr 編譯 MFC 和 ATL 程式碼
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], interoperability
- ATL [C++], interoperability
- mixed assemblies [C++], MFC code
- mixed assemblies [C++], ATL code
- /clr compiler option [C++], compiling ATL and MFC code
- interoperability [C++], /clr compiler option
- regular MFC DLLs [C++], /clr compiler option
- interop [C++], /clr compiler option
- extension DLLs [C++], /clr compiler option
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
ms.openlocfilehash: 9a24e82787eb0fce8ff668843e73de9f2d05e1ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379037"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>HOW TO：編譯 MFC 和 ATL 程式碼使用 /clr

本主題討論如何編譯現有的 MFC 和 ATL 程式為目標的通用語言執行平台。

### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>若要使用 /clr 編譯 MFC 可執行檔或一般 MFC DLL

1. 中的專案上按一下滑鼠右鍵**方案總管**，然後按一下**屬性**。

1. 在 **專案屬性**對話方塊方塊中，依序展開節點旁**組態屬性**，然後選取**一般**。 在右窗格中，在**專案預設值**，將**Common Language Runtime 支援**來**Common Language Runtime 支援 (/ clr)**。

   在相同的窗格中，請確定**MFC 用法**設為**使用 MFC 的共用 dll**。

1. 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**一般**。 請確定**偵錯資訊格式**設為**程式資料庫 /Zi** (不 **/ZI**)。

1. 選取 **程式碼產生**節點。 設定**啟用最少重建**要**否 (/ /gm-)**。 Ssprop_param_table_default**基本執行階段會檢查**要**預設**。

1. 底下**組態屬性**，選取**C /C++** 再**程式碼產生**。 請確定**執行階段程式庫**會設為**多執行緒偵錯 DLL (/ /mdd)** 或是**多執行緒 DLL (/ MD)**。

1. 在 Stdafx.h 中加入下面這一行。

    ```
    #using <System.Windows.Forms.dll>
    ```

### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>若要使用 /clr 編譯 MFC 擴充 DLL

1. 請依照 「 若要編譯 MFC 可執行檔或一般 MFC DLL 使用 /clr 」 中的步驟。

1. 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**先行編譯標頭**。 設定**建立/使用先行編譯標頭**要**未使用先行編譯標頭**。

   或者，在**方案總管**Stdafx.cpp 上按一下滑鼠右鍵，然後按一下 **屬性**。 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**一般**。 設定**Common Language Runtime 支援編譯**要**Common Language Runtime 不支援**。

1. 檔案包含 DllMain 和任何項目呼叫，在**方案總管**，以滑鼠右鍵按一下檔案，然後按一下**屬性**。 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**一般**。 在右窗格中下,**專案預設值**，將**Common Language Runtime 支援編譯**來**No Common Language Runtime 支援**。

### <a name="to-compile-an-atl-executable-by-using-clr"></a>若要使用 /clr 編譯 ATL 可執行檔

1. 在 **方案總管**，以滑鼠右鍵按一下專案，然後按一下**屬性**。

1. 在 **專案屬性**對話方塊方塊中，依序展開節點旁**組態屬性**，然後選取**一般**。 在右窗格中，在**專案預設值**，將**Common Language Runtime 支援**來**Common Language Runtime 支援 (/ clr)**。

1. 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**一般**。 請確定**偵錯資訊格式**設為**程式資料庫 /Zi** (不 **/ZI**)。

1. 選取 **程式碼產生**節點。 設定**啟用最少重建**要**否 (/ /gm-)**。 Ssprop_param_table_default**基本執行階段會檢查**要**預設**。

1. 底下**組態屬性**，選取**C /C++** 再**程式碼產生**。 請確定**執行階段程式庫**會設為**多執行緒偵錯 DLL (/ /mdd)** 或是**多執行緒 DLL (/ MD)**。

1. 針對每個 MIDL 產生檔案 （C 檔案），以滑鼠右鍵按一下中的檔案**方案總管**，然後按一下**屬性**。 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**一般**。 設定**Common Language Runtime 支援編譯**要**Common Language Runtime 不支援**。

### <a name="to-compile-an-atl-dll-by-using-clr"></a>若要使用 /clr 編譯 ATL DLL

1. 請遵循 < 使用 /clr 編譯 ATL 可執行檔 」 一節中的步驟。

1. 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**先行編譯標頭**。 設定**建立/使用先行編譯標頭**要**未使用先行編譯標頭**。

   或者，在**方案總管**Stdafx.cpp 上按一下滑鼠右鍵，然後按一下 **屬性**。 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**一般**。 設定**Common Language Runtime 支援編譯**要**Common Language Runtime 不支援**。

1. 檔案包含 DllMain 和任何項目呼叫，在**方案總管**，以滑鼠右鍵按一下檔案，然後按一下**屬性**。 底下**組態屬性**，依序展開節點旁**C /C++**  ，然後選取**一般**。 在右窗格中下,**專案預設值**，將**Common Language Runtime 支援編譯**來**No Common Language Runtime 支援**。

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
