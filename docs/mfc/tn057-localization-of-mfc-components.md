---
title: "TN057: MFC 元件的當地語系化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.components
dev_langs: C++
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e27b737a76b30e7193a9afb7797a20951294032e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn057-localization-of-mfc-components"></a>TN057：MFC 元件的當地語系化
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 此提示會描述一些您可以用來當地語系化元件 (如果該元件是一個應用程式或 OLE 控制項，或是使用 MFC 的 DLL) 的設計和程序。  
  
## <a name="overview"></a>總覽  
 在當地語系化使用 MFC 的元件時，有兩個問題需要解決。 首先，您必須當地語系化您的資源，即字串、對話方塊和專屬於您元件的其他資源。 大部分使用 MFC 建置的元件也包括並使用許多由 MFC 定義的資源。 您也必須提供當地語系化的 MFC 資源。 所幸，MFC 本身已經提供數種語言。  
  
 此外，您應該準備好在其目標環境下執行元件 (歐洲或支援 DBCS 的環境)。 在大部分的情況下，這取決於您的應用程式如何正確處理設定高位元的字元，以及如何處理使用雙位元組字元的字串。 根據預設，在啟用 MFC 時，針對這兩種環境，可以在所有平台上使用單一的全球二進位檔，同時在安裝時插入不同的資源。  
  
## <a name="localizing-your-components-resources"></a>當地語系化元件的資源  
 當地語系化您的應用程式或 DLL 應該只包含使用符合目標語言的資源取代資源。 對於您自己的資源，這是相當簡單的一件事：在資源編輯器中編輯資源並建置應用程式即可。 如果您的程式碼撰寫正確，會有任何字串或文字，您需要透過硬式編碼方式在 c + + 原始程式碼-可以透過修改資源來完成所有當地語系化。 實際上，您可以實作自己的元件，這類元件可提供當地語系化版本，其中甚至不包含原始程式碼的組建。 這種方式較為更複雜，不過卻很值得，同時這種方法也是 MFC 所選擇使用的機制。 藉由直接載入 EXE 或 DLL 檔案至資源編輯器並編輯資源，也可以當地語系化應用程式。 其中也有可能需要在每次建置應用程式的新版本時，對這些變更重新建置應用程式。  
  
 其中一種避免此種情形的方式是在個別的 DLL (有時稱為附屬 DLL) 中放置所有資源。 這個 DLL 會在執行階段動態地載入，而資源會從該 DLL 載入，而不是從內含所有程式碼的主要模組載入。 MFC 直接支援這個方法。 請考量當應用程式呼叫 MYAPP.EXE 時，它的資源可能是從名為 MYRES.DLL 的 DLL 所載入。 在應用程式的 `InitInstance` 中，它將會執行下列程式碼以載入該 DLL，並使 MFC 從該位置載入資源：  
  
```  
CMyApp::InitInstance()  
{ *// one of the first things in the init code  
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)  
    AfxSetResourceHandle(hInst);

 *// other initialization code would follow  
 .  
 .  
 .  
}  
```  
  
 從該時間點之後，MFC 將會從該 DLL 載入資源，而不是從 myapp.exe 載入資源。 不過，所有資源必須存在於該 DLL 中，MFC 不會在尋找特定資源時搜尋應用程式的執行個體。 這項技術會套用至同樣標準 MFC Dll 以及 OLE 控制項。 您的安裝程式會將根據使用者所需的資源地區設定來複製正確的 MYRES.DLL 版本。  
  
 相較之下，建立僅含資源的 DLL 是相當容易的。 您會建立一個 DLL 專案，加入 .RC 檔至該專案，並加入所需的資源。 如果您擁有未使用這個技巧的現有專案，可以從該專案複製資源。 將資源檔加入專案之後，您幾乎已經準備好可以建立專案了。 唯一您必須執行的是設定連結器選項，以包含**/NOENTRY**。 這麼做會告訴連結器該 DLL 沒有進入點-因為沒有程式碼，它會有任何進入點。  
  
> [!NOTE]
>  在 Visual C++ 4.0 (含) 以上版本的資源編輯器支援多種語言的 .RC。 這使得您可以非常容易地在單一專案中管理當地語系化。 每種語言的資源是由資源編輯器所產生的前置處理器指示詞加以控制。  
  
## <a name="using-the-provided-mfc-localized-resources"></a>使用所提供的 MFC 當地語系化資源  
 您建立的任何 MFC 應用程式都會重複使用 MFC 的兩項東西：程式碼和資源。 也就是說，MFC 具有的各種錯誤訊息、內建對話方塊和 MFC 類別所使用的其他資源。 為了完全當地語系化您的應用程式，您不僅需要當地語系化應用程式中的資源，也要當地語系化直接取自 MFC 的資源。 MFC 會自動提供許多不同語言的資源檔，因此，如果您的目標語言屬於 MFC 所支援的其中一種語言，則您只需確定所使用的是這些當地語系化的資源。  
  
 在撰寫本文時，MFC 支援中文、德文、西班牙文、法文、義大利文、日文和韓文。 包含這些當地語系化版本的檔案位於 MFC\INCLUDE\L.* ('L' 代表當地語系化) 目錄中。 例如德文檔案位於 MFC\INCLUDE\L.DEU 中。 若要讓應用程式使用這些 RC 檔案，而不是位於 MFC\INCLUDE 中的檔案，加入`/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU`RC 的命令列 （這只是範例，您需要取代您的地區設定的選項，以及安裝 Visual C 所在的目錄++).  
  
 如果您的應用程式以靜態方式與 MFC 進行連結，則可以使用上述方式。 大部分的應用程式會以動態方式進行連結 (因為這是 AppWizard 的預設值)。 在此案例中，程式碼是以動態方式連結的資源皆。 因此，您可以當地語系化應用程式中的資源，不過，MFC 實作資源仍會從 MFC7x.DLL (或更新版本) 或從 MFC7xLOC.DLL 載入 (如果有的話)。 您可以從兩個不同的角度來探討這一點。  
  
 較複雜的方法是銷售其中一種當地語系化的 MFC7xLOC.DLL (例如德文的 MFC7xDEU、西班牙文的 MFC7xESP.DLL 等) 或更新版本，並在使用者安裝應用程式時安裝適當的 MFC7xLOC.DLL 至系統目錄。 這對於開發人員和終端使用者而言非常複雜，不建議採用此種方法。 請參閱[技術提示 56](../mfc/tn056-installation-of-localized-mfc-components.md)如需此技術及其警告的詳細資訊。  
  
 最簡單且最安全的方法是將當地語系化的 MFC 資源放在應用程式或 DLL (或其附屬 DLL，如果您有使用的話) 中。 這麼做可避免安裝正確版本 MFC7xLOC.DLL 的問題。 若要這麼做，請按照上述與靜態連結狀況相同的指示執行 (正確地將 RC 命令列設定為指向當地語系化的資源)，不過，您還必須移除預設由 AppWizard 加入的 `/D_AFXDLL` 定義。 當定義了 `/D_AFXDLL` 時，AFXRES.H (和其他 MFC RC 檔案) 實際上不會定義任何資源 (因為改從 MFC DLL 提取它會)。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

