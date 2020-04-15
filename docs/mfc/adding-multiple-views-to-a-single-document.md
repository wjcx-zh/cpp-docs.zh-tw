---
title: 將多個檢視加入至單一文件
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 4fa39a4d9369c84d2cffdaeff28dc9cb2f966b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370859"
---
# <a name="adding-multiple-views-to-a-single-document"></a>將多個檢視加入至單一文件

在與 Microsoft 基礎類 (MFC) 庫建立的單文檔介面 (SDI) 應用程式中,每個文件類型都與單個視圖類型相關聯。 在某些情況下,最好能夠將文檔的當前視圖與新檢視切換。

> [!TIP]
> 有關為單個文件實現多個檢視的其他過程,請參閱[CDocument:AddView](../mfc/reference/cdocument-class.md#addview)和[COLLECT](../overview/visual-cpp-samples.md) MFC 範例。

您可以通過添加`CView`新 派生類和其他代碼來動態將視圖切換到現有的 MFC 應用程式來實現此功能。

步驟如下：

- [變更現有應用程式類別](#vcconmodifyexistingapplicationa1)

- [建立與修改新的檢視類別](#vcconnewviewclassa2)

- [建立並附加新的檢視](#vcconattachnewviewa3)

- [切換切換功能](#vcconswitchingfunctiona4)

- [新增對切換檢視](#vcconswitchingtheviewa5)

本主題的其餘部分假定以下內容:

- `CWinApp`派生物件的名稱為`CMyWinApp`,`CMyWinApp`並在 MYWINAPP 中聲明和定義 *。H*和*MYWINAPP。CPP*.

- `CNewView`是新`CView`派生物件的名稱`CNewView`, 並在*NEWVIEW 中聲明和定義。H*和*NEWVIEW。CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>變更現有應用程式類別

要使應用程式在檢視之間切換,您需要透過添加成員變數來儲存檢視和切換它們的方法來修改應用程式類。

將以下代碼添加到`CMyWinApp`*MYWINAPP 中的聲明。H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

新成員變數 和`m_pOldView``m_pNewView`指向當前檢視和新創建的檢視。 當使用者請求時,`SwitchView`新方法 ( ) 會切換檢視。 該方法的主體在稍後的「[實現切換函數」](#vcconswitchingfunctiona4)中討論了本主題。

對應用程式類的最後一次修改需要包括一個新的標頭檔,該檔定義在切換函數中使用的 Windows 消息 **(WM_INITIALUPDATE)。**

在 MYWINAPP 的包含部分中插入以下行 *。CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

保存更改並繼續下一步。

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>建立與修改新的檢視類別

通過使用類檢視中可用的**New Class**命令,創建新檢視類變得容易。 此類的唯一要求是它派生自`CView`。 將此新類添加到應用程式。 有關向專案新增新類別的特定資訊,請參閱[新增類別](../ide/adding-a-class-visual-cpp.md)。

將類添加到專案后,需要更改某些視圖類成員的可訪問性。

修改*新視圖。H*通過將訪問指定器從**保護**更改為**公共**構造函數和析構函數。 這允許動態創建和銷毀類,並在視圖可見之前對其進行修改。

保存更改並繼續下一步。

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>建立並附加新的檢視

要創建和附加新檢視,需要修改應用程式類的`InitInstance`函數。 修改添加了新代碼,該代碼創建新的檢視物件,然後初始化兩個`m_pOldView`現有`m_pNewView`視圖物件。

由於新檢視是在函數中創建的,`InitInstance`因此新檢視和現有檢視都會在應用程式的生存期內保留。 但是,應用程式同樣可以輕鬆地動態創建新視圖。

呼叫 後插入此代碼`ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

保存更改並繼續下一步。

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>切換切換功能

在上一步中,您添加了創建和初始化新檢視對象的代碼。 最後一個主要部分是實現交換方法。 `SwitchView`

在應用程式類別 ( MYWINAPP) 的完整檔案的末尾 *。CPP*),新增以下方法定義:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

保存更改並繼續下一步。

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>新增對切換檢視

最後一步是在應用程式需要在檢視之間切換`SwitchView`時添加調用方法的代碼。 這可以通過多種方式完成:通過添加新菜單項供用戶選擇,或在滿足某些條件時在內部切換視圖。

有關新增新選單項目與指令處理程式函數的詳細資訊,請參考[指令與控制通知的處理程式](../mfc/handlers-for-commands-and-control-notifications.md)。

## <a name="see-also"></a>另請參閱

[文件/檢視體系結構](../mfc/document-view-architecture.md)
