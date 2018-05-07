---
title: 如何： 使用 clr 編譯 MFC 和 ATL 程式碼 |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7412d69230bcb6375a042d6cf8e8f27a3d9eac9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>如何：使用 /clr 編譯 MFC 和 ATL 程式碼
本主題討論如何編譯現有的 MFC 和 ATL 程式為目標的通用語言執行平台。  
  
### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>若要使用 /clr 編譯 MFC 可執行檔或一般 MFC 的 DLL  
  
1.  中的專案上按一下滑鼠右鍵**方案總管] 中**，然後按一下 [**屬性**。  
  
2.  在**專案屬性**對話方塊方塊中，展開節點旁**組態屬性**選取**一般**。 在右窗格中下,**專案預設值**，將**Common Language Runtime 支援**至**Common Language Runtime 支援 (/ clr)**。  
  
     在相同的窗格中，請確定**MFC**設**使用 MFC 的共用 dll**。  
  
3.  下**組態屬性**，依序展開節點旁**C/c + +** 選取**一般**。 請確定**偵錯資訊格式**設**程式資料庫 /Zi** (不 **/ZI**)。  
  
4.  選取**程式碼產生**節點。 設定**啟用最少重建**至**否 (/ Gm-)**。 也設定**基本執行階段會檢查**至**預設**。  
  
5.  在下**組態屬性**，選取**C/c + +** 然後**程式碼產生**。 請確定**執行階段程式庫**會設為**多執行緒偵錯 DLL (/ /mdd)** 或**多執行緒 DLL (/ MD)**。  
  
6.  在 Stdafx.h，加入下列一行。  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>若要使用 /clr 編譯 MFC 擴充 DLL  
  
1.  請遵循 「 若要編譯 MFC 可執行檔或一般 MFC DLL 使用 /clr"中的步驟。  
  
2.  下**組態屬性**，依序展開節點旁**C/c + +** 選取**先行編譯標頭**。 設定**建立/使用先行編譯標頭**至**未使用先行編譯標頭**。  
  
     或者，在**方案總管 中**Stdafx.cpp 上按一下滑鼠右鍵，然後按**屬性**。 下**組態屬性**，依序展開節點旁**C/c + +** 選取**一般**。 設定**使用 Common Language Runtime 支援編譯**至**否 Common Language Runtime 支援**。  
  
3.  檔案包含 DllMain 和任何項目呼叫，在**方案總管 中**，以滑鼠右鍵按一下檔案，然後按一下**屬性**。 下**組態屬性**，依序展開節點旁**C/c + +** 選取**一般**。 在右窗格中，在**專案預設值**，將**使用 Common Language Runtime 支援編譯**至**否 Common Language Runtime 支援**。  
  
### <a name="to-compile-an-atl-executable-by-using-clr"></a>若要使用 /clr 編譯 ATL 可執行檔  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下專案，然後按一下**屬性**。  
  
2.  在**專案屬性**對話方塊方塊中，展開節點旁**組態屬性**選取**一般**。 在右窗格中下,**專案預設值**，將**Common Language Runtime 支援**至**Common Language Runtime 支援 (/ clr)**。  
  
3.  下**組態屬性**，依序展開節點旁**C/c + +** 選取**一般**。 請確定**偵錯資訊格式**設**程式資料庫 /Zi** (不 **/ZI**)。  
  
4.  選取**程式碼產生**節點。 設定**啟用最少重建**至**否 (/ Gm-)**。 也設定**基本執行階段會檢查**至**預設**。  
  
5.  在下**組態屬性**，選取**C/c + +** 然後**程式碼產生**。 請確定**執行階段程式庫**會設為**多執行緒偵錯 DLL (/ /mdd)** 或**多執行緒 DLL (/ MD)**。  
  
6.  針對每個 MIDL 所產生的檔案 （C 檔案），以滑鼠右鍵按一下中的檔案**方案總管] 中**，然後按一下 [**屬性**。 下**組態屬性**，依序展開節點旁**C/c + +** 選取**一般**。 設定**使用 Common Language Runtime 支援編譯**至**否 Common Language Runtime 支援**。  
  
### <a name="to-compile-an-atl-dll-by-using-clr"></a>若要使用 /clr 編譯 ATL DLL  
  
1.  請依照下列中的 「 使用 /clr 編譯 ATL 可執行檔 」 一節的步驟。  
  
2.  下**組態屬性**，依序展開節點旁**C/c + +** 選取**先行編譯標頭**。 設定**建立/使用先行編譯標頭**至**未使用先行編譯標頭**。  
  
     或者，在**方案總管 中**Stdafx.cpp 上按一下滑鼠右鍵，然後按**屬性**。 下**組態屬性**，依序展開節點旁**C/c + +** 選取**一般**。 設定**使用 Common Language Runtime 支援編譯**至**否 Common Language Runtime 支援**。  
  
3.  檔案包含 DllMain 和任何項目呼叫，在**方案總管 中**，以滑鼠右鍵按一下檔案，然後按一下**屬性**。 下**組態屬性**，依序展開節點旁**C/c + +** 選取**一般**。 在右窗格中，在**專案預設值**，將**使用 Common Language Runtime 支援編譯**至**否 Common Language Runtime 支援**。  
  
## <a name="see-also"></a>另請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)