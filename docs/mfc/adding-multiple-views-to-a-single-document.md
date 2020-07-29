---
title: 將多個檢視加入至單一文件
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 95de3a582c3d45db858e2b4bce0268e1dab63931
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215968"
---
# <a name="adding-multiple-views-to-a-single-document"></a>將多個檢視加入至單一文件

在使用 Microsoft Foundation Class （MFC）程式庫建立的單一檔介面（SDI）應用程式中，每個檔案類型都與單一檢視類型相關聯。 在某些情況下，最好能夠以新的視圖來切換檔的目前視圖。

> [!TIP]
> 如需針對單一檔執行多個視圖的其他程式，請參閱[CDocument：： AddView](reference/cdocument-class.md#addview)和[COLLECT](../overview/visual-cpp-samples.md) MFC 範例。

您可以藉由加入新 `CView` 衍生的類別和額外的程式碼，將視圖動態切換至現有的 MFC 應用程式來執行此功能。

步驟如下：

- [修改現有的應用程式類別](#vcconmodifyexistingapplicationa1)

- [建立和修改新的 View 類別](#vcconnewviewclassa2)

- [建立並附加新的視圖](#vcconattachnewviewa3)

- [執行切換函式](#vcconswitchingfunctiona4)

- [新增切換視圖的支援](#vcconswitchingtheviewa5)

本主題的其餘部分會假設下列各項：

- 衍生物件的名稱 `CWinApp` 是 `CMyWinApp` ，而且 `CMyWinApp` 會在 MYWINAPP 中宣告和定義 *。H*和*MYWINAPP。CPP*。

- `CNewView`這是新 `CView` 衍生物件的名稱，而且 `CNewView` 會在 NEWVIEW 中宣告和定義 *。H*和*NEWVIEW。CPP*。

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>修改現有的應用程式類別

若要讓應用程式在 views 之間切換，您需要新增成員變數來修改應用程式類別，以儲存視圖，並使用方法來切換它們。

將下列程式碼新增至 `CMyWinApp` MYWINAPP 中的宣告 *。H*：

[!code-cpp[NVC_MFCDocViewSDI#1](codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

新的成員變數， `m_pOldView` 和會 `m_pNewView` 指向目前的視圖和新建立的。 新方法（）會在 `SwitchView` 使用者要求時切換 views。 本主題稍後的「[執行切換](#vcconswitchingfunctiona4)」函式會討論方法的主體。

最後一次修改應用程式類別時，需要包含新的標頭檔，該檔案會定義切換函式中使用的 Windows 訊息（**WM_INITIALUPDATE**）。

在 MYWINAPP 的 include 區段中插入下列這一行 *。CPP*：

[!code-cpp[NVC_MFCDocViewSDI#2](codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

儲存您的變更，並繼續進行下一個步驟。

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>建立和修改新的 View 類別

使用類別檢視提供的**新類別**命令，可以輕鬆地建立新的 view 類別。 此類別的唯一需求是它衍生自 `CView` 。 將這個新類別加入應用程式。 如需將新類別新增至專案的特定資訊，請參閱[加入類別](../ide/adding-a-class-visual-cpp.md)。

將類別加入至專案之後，您必須變更某些 view 類別成員的存取範圍。

修改*NEWVIEW。H* ，方法是將此存取規範從變更為， **`protected`** **`public`** 針對此函式和析構函數。 這可讓您以動態方式建立和終結類別，並在顯示之前修改視圖外觀。

儲存您的變更，並繼續進行下一個步驟。

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>建立並附加新的視圖

若要建立並附加新的視圖，您需要修改 `InitInstance` 應用程式類別的功能。 修改會加入新的程式碼，以建立新的 view 物件， `m_pOldView` 然後 `m_pNewView` 使用兩個現有的 view 物件來初始化和。

因為新的視圖是在函式內建立的 `InitInstance` ，所以新的和現有的視圖都會保存在應用程式的存留期。 不過，應用程式可以輕鬆地以動態方式建立新的視圖。

在呼叫之後插入此程式碼 `ProcessShellCommand` ：

[!code-cpp[NVC_MFCDocViewSDI#3](codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

儲存您的變更，並繼續進行下一個步驟。

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>執行切換函式

在上一個步驟中，您已新增程式碼，以建立並初始化新的 view 物件。 最後一個主要部分是執行切換方法 `SwitchView` 。

在應用程式類別的執行檔結尾處（*MYWINAPP。CPP*），新增下列方法定義：

[!code-cpp[NVC_MFCDocViewSDI#4](codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

儲存您的變更，並繼續進行下一個步驟。

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>新增切換視圖的支援

最後一個步驟包括新增程式碼， `SwitchView` 以在應用程式需要切換 views 時呼叫方法。 這可以透過數種方式來完成：加入新的功能表項目，供使用者在符合特定條件時于內部選擇或切換視圖。

如需有關加入新功能表項目和命令處理常式函式的詳細資訊，請參閱[命令和控制項通知的處理常式](handlers-for-commands-and-control-notifications.md)。

## <a name="see-also"></a>另請參閱

[檔/視圖架構](document-view-architecture.md)
