---
title: 將多個檢視加入至單一文件
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 593c59c73b58b4364c9d652ce8eb415c17af496c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767583"
---
# <a name="adding-multiple-views-to-a-single-document"></a>將多個檢視加入至單一文件

使用 Microsoft Foundation Class (MFC) 程式庫建立單一文件介面 (SDI) 應用程式中，每個文件類型是與單一的檢視類型相關聯。 在某些情況下，最好能夠切換文件的新檢視目前的檢視。

> [!TIP]
>  如需實作單一文件的多個檢視的其他程序，請參閱 < [CDocument::AddView](../mfc/reference/cdocument-class.md#addview)並[收集](../overview/visual-cpp-samples.md)MFC 範例。

您可以實作這項功能加入新`CView`-衍生的類別和其他程式碼以動態方式將檢視切換至現有的 MFC 應用程式。

步驟如下所示：

- [修改現有的應用程式類別](#vcconmodifyexistingapplicationa1)

- [建立和修改新的檢視類別](#vcconnewviewclassa2)

- [建立並附加新的檢視](#vcconattachnewviewa3)

- [實作切換函式](#vcconswitchingfunctiona4)

- [新增支援將檢視切換](#vcconswitchingtheviewa5)

本主題的其餘部分假設如下：

- 名稱`CWinApp`-衍生的物件`CMyWinApp`，並`CMyWinApp`宣告和定義在*MYWINAPP。H*和*MYWINAPP。CPP*。

- `CNewView` 是的新名稱`CView`-衍生的物件，並`CNewView`宣告和定義在*NEWVIEW。H*和*NEWVIEW。CPP*。

##  <a name="vcconmodifyexistingapplicationa1"></a> 修改現有的應用程式類別

切換檢視應用程式，您要新增成員變數來儲存檢視和方法，以將其切換以修改應用程式類別。

將下列程式碼新增至宣告`CMyWinApp`在*MYWINAPP。H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

新成員變數`m_pOldView`和`m_pNewView`，指向目前的檢視和新建的一個。 新的方法 (`SwitchView`) 切換檢視，當使用者要求。 方法的主體會在本主題稍後討論[實作切換函式](#vcconswitchingfunctiona4)。

上次修改應用程式類別必須包括定義 Windows 訊息的新標頭檔 (**WM_INITIALUPDATE**) 切換函式中使用。

包含一節中插入下面這一行*MYWINAPP。CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

儲存變更，並繼續下一個步驟。

##  <a name="vcconnewviewclassa2"></a> 建立和修改新的檢視類別

建立新的檢視類別更容易使用**新的類別**類別檢視中可用的命令。 這個類別的唯一需求是它會衍生自`CView`。 將這個新類別新增至 應用程式。 如需將新類別加入至專案的特定資訊，請參閱[加入類別](../ide/adding-a-class-visual-cpp.md)。

一旦您將類別加入至專案，您需要變更的部分檢視類別成員存取範圍。

修改*NEWVIEW。H*藉由變更存取指定名稱，從**保護**要**公用**建構函式和解構函式。 這可讓類別來建立和終結動態和修改檢視外觀，才能顯示。

儲存變更，並繼續下一個步驟。

##  <a name="vcconattachnewviewa3"></a> 建立並附加新的檢視

若要建立並附加新的檢視，您需要修改`InitInstance`函式的應用程式類別。 修改會將新的程式碼會建立新的檢視物件，然後初始化這兩個`m_pOldView`和`m_pNewView`與兩個現有的檢視物件。

因為在建立新的檢視`InitInstance`函式，這兩個新的和現有檢視保存應用程式的存留期。 不過，應用程式可以輕鬆地以動態方式建立新的檢視。

在呼叫之後插入此程式碼`ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

儲存變更，並繼續下一個步驟。

##  <a name="vcconswitchingfunctiona4"></a> 實作切換函式

在上一個步驟中，您可以加入程式碼，建立並初始化新的檢視物件。 最後的主要部分是實作切換的方法， `SwitchView`。

在您的應用程式類別的實作檔案結尾 (*MYWINAPP。CPP*)，新增下列方法定義：

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

儲存變更，並繼續下一個步驟。

##  <a name="vcconswitchingtheviewa5"></a> 新增支援將檢視切換

最後一個步驟牽涉到將呼叫的程式碼加入`SwitchView`方法時，應用程式需要檢視之間切換。 這可以透過數種方式： 藉由讓使用者選擇 [新增] 功能表項目，或符合特定條件時，內部切換檢視。

如需有關加入新的功能表項目和命令處理常式函式的詳細資訊，請參閱[命令和控制項告知處理常式](../mfc/handlers-for-commands-and-control-notifications.md)。

## <a name="see-also"></a>另請參閱

[文件/檢視架構](../mfc/document-view-architecture.md)
