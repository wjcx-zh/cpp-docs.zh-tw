---
title: "TN020: ID 命名和編號慣例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.id
dev_langs: C++
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a666c2183276b95a9405400de8acc0117c7134e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020：ID 命名和編號慣例
此提示說明 ID 命名和編號慣例 MFC 2.0 使用的資源、 命令、 字串、 控制項和子視窗。  
  
 MFC ID 命名和編號慣例被要符合下列需求：  
  
-   提供 MFC 程式庫和 MFC 應用程式所支援的 Visual c + + 資源編輯器使用一致的識別碼命名標準。 這讓程式設計人員解譯的類型和來源的資源識別碼中更容易  
  
-   強調特定類型的識別碼之間的強式 1 對 1 關聯性。  
  
-   符合已廣泛使用的標準命名 Windows 中的識別碼。  
  
-   資料分割識別碼編號的空間。 識別碼可由程式設計人員、 MFC、 Windows 和 Visual c + + 編輯的資源指派。 適當的資料分割，有助於避免重複的識別碼號碼。  
  
## <a name="the-id-prefix-naming-convention"></a>識別碼前置詞命名慣例  
 應用程式可能會發生數種類型的識別碼。 MFC 識別碼命名慣例定義不同的資源類型的不同前置詞。  
  
 MFC 使用的前置詞"IDR_"，表示適用於多個資源類型的資源識別碼。 比方說，針對指定的框架視窗中，MFC 會使用相同的 「 IDR_"前置詞，表示功能表、 快速鍵、 字串和圖示的資源。 下表顯示各種不同的前置詞和其使用方式：  
  
|前置詞|使用|  
|------------|---------|  
|IDR_|多個資源類型 （主要是用於功能表、 加速器以及功能區）。|  
|IDD_|對話方塊範本資源 (例如 IDD_DIALOG1)。|  
|IDC_|如需資料指標的資源。|  
|IDI_|如需圖示資源。|  
|IDB_|若為點陣圖的資源。|  
|IDS_|字串資源。|  
  
 內對話方塊資源，MFC 會遵循下列慣例：  
  
|前置詞或標籤|使用|  
|---------------------|---------|  
|IDOK IDCANCEL|標準的推播按鈕 Id。|  
|IDC_|其他對話方塊控制項。|  
  
 資料指標，也會使用 「 IDC_"前置詞。 這個命名的衝突通常不問題因為一般應用程式會有幾個游標及許多對話方塊控制項。  
  
 內功能表資源，MFC 會遵循下列慣例：  
  
|前置詞|使用|  
|------------|---------|  
|IDM_|不使用 MFC 命令架構的功能表項目。|  
|ID_|使用 MFC 的功能表命令的命令架構。|  
  
 遵循 MFC 命令架構的命令必須有`ON_COMMAND`命令處理常式，而且可以有`ON_UPDATE_COMMAND_UI`處理常式。 如果這些命令處理常式會遵循 MFC 命令架構，它們將會正常運作是否它們繫結至功能表命令、 工具列按鈕或對話方塊列按鈕。 相同的 「 ID_"前置詞也用於顯示在程式的訊息列中的功能表提示字串。 大部分應用程式中的功能表項目應該遵循的 MFC 命令慣例。 所有標準命令 Id (例如， `ID_FILE_NEW`) 遵循這個慣例。  
  
 MFC 也會使用 「 IDP_"做為一種特殊形式的字串 （而不是"IDS_")。 "IDP_"前置詞的字串會出現提示，也就是在訊息方塊中所使用的字串。 以預留位置表示字串取決於程式的"IDP_"字串可以包含"%1"和"%2"。 「 IDP_"字串通常會有與其相關聯的說明主題，且 「 IDS_"字串。 一律當地語系化"IDP_"字串，並 「 IDS_"字串可能不會進行當地語系化。  
  
 MFC 程式庫也會使用 「 IDW_"前置詞為一種特殊形式的控制項 Id （而不是"IDC_")。 這些識別碼指派給子視窗，例如檢視和分隔器的架構類別。 MFC 實作識別碼有前置"AFX_"。  
  
## <a name="the-id-numbering-convention"></a>識別碼編號慣例  
 下表列出針對特定類型之識別碼的有效範圍。 某些限制的技術限制，且其他的則是設計來防止您的 Id 正在與 Windows 預先定義的 Id 或 MFC 實作預設的慣例。  
  
 我們強烈建議您定義建議的範圍內的所有識別碼。 這些範圍的下限為 1，因為不是 0。 我們建議您使用的常見慣例，並使用 100 或 101 作為第一個識別碼。  
  
|前置詞|資源類型|有效範圍|  
|------------|-------------------|-----------------|  
|IDR_|多個|1 至 0x6FFF|  
|IDD_|對話方塊範本|1 至 0x6FFF|  
|IDC_，IDI_，IDB_|資料指標、 圖示、 點陣圖|1 至 0x6FFF|  
|IDS_ IDP_|一般字串|1 到 0x7FFF|  
|ID_|命令|0x8000 至 0xDFFF|  
|IDC_|控制項|8 到 0xDFFF|  
  
 這些範圍限制的原因：  
  
-   依照慣例，不使用的識別碼值為 0。  
  
-   Windows 實作的限制，則為 true 的資源必須小於或等於 0x7FFF 的識別碼。  
  
-   MFC 的內部架構會保留這些範圍：  
  
    -   透過 0x7FFF 0x7000 （請參閱 afxres.h）  
  
    -   透過 0xEFFF 0xE000 （請參閱 afxres.h）  
  
    -   16000 透過 18000 （請參閱 afxribbonres.h）  
  
     這些範圍可能在未來變更 MFC 實作。  
  
-   Windows 系統的數個命令使用 0xF000 到 0xFFFF 的範圍。  
  
-   1 到 7 的控制項 Id 被保留給 IDCANCEL IDOK 等標準控制項。  
  
-   0x8000 到字串 0xFFFF 的範圍被保留給命令的功能表提示。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

