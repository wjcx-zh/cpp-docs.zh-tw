---
title: 使用文件資料變數管理資料
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: 3d845b0fc3d00369d44c21c04a3fb7e3b8d6189e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618330"
---
# <a name="managing-data-with-document-data-variables"></a>使用文件資料變數管理資料

將您的檔資料實作為檔類別的成員變數。 例如，「曲線」程式會宣告類型的資料成員 `CObList` ，也就是用來儲存物件指標的連結清單 `CObject` 。 這份清單用來儲存構成手繪線繪製的點陣列。

您要如何執行檔的成員資料，取決於應用程式的本質。 為了協助您瞭解，MFC 提供了一組「集合類別」，陣列、清單和對應（字典），包括以 c + + 範本為基礎的集合，以及封裝各種常見資料類型（例如 `CString` 、 `CRect` 、 `CPoint` 、和） `CSize` 的類別 `CTime` 。 如需這些類別的詳細資訊，請參閱*MFC 參考*中的[類別庫總覽](class-library-overview.md)。

當您定義檔的成員資料時，通常會將成員函式新增至檔類別，以設定及取得資料項目，並對它們執行其他有用的作業。

您的 views 會使用檔的視圖指標來存取檔物件，並在建立時于視圖中安裝。 您可以藉由呼叫成員函式，在視圖的成員函式中抓取此指標 `CView` `GetDocument` 。 請務必將此指標轉換成您自己的檔案類型。 然後您就可以透過指標來存取公用檔成員。

如果頻繁的資料傳輸需要直接存取，或您想要使用 document 類別的非公用成員，您可能會想要讓 view 類別成為檔類別的 friend （c + + 詞彙）。

## <a name="see-also"></a>另請參閱

[使用文件](using-documents.md)
