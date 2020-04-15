---
title: MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: 41ac0180242aea3143a1df2c32dc81fb18cd7dca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370785"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結

ActiveX 控制項的功能更強大的用途是資料綁定,它允許控制項的屬性與資料庫中的特定欄位綁定。 當使用者修改此綁定屬性中的數據時,控件會通知資料庫並請求更新記錄欄位。 然後,資料庫通知對請求成功或失敗的控制。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

本文介紹任務的控制側。 實現與資料庫的數據綁定交互是控制容器的責任。 如何管理容器中的資料庫交互超出了本文檔的範圍。 本文的其餘部分介紹了如何準備數據綁定控件。

![資料&#45;繫結件的概念圖](../mfc/media/vc374v1.gif "資料&#45;繫結件的概念圖") <br/>
資料繫結控制的概念圖

該`COleControl`類提供了兩個成員函數,使數據綁定成為易於實現的過程。 第一個函數[綁定屬性請求編輯](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)用於請求更改屬性值的許可權。 [綁定屬性更改](../mfc/reference/colecontrol-class.md#boundpropertychanged),第二個函數,在屬性值成功更改後調用。

本文章涵蓋下列主題：

- [建立可結合的權屬性](#vchowcreatingbindablestockproperty)

- [建立可結合取得/集方法](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>建立可結合的權屬性

可以建立資料繫結的股票屬性,儘管您更有可能需要[一個可綁定的 get/set 方法](#vchowcreatingbindablegetsetmethod)。

> [!NOTE]
> 默認情況下,股票屬性`bindable`具有`requestedit`和屬性。

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>使用新增屬性精靈新增可繫定的庫存屬性

1. 使用[MFC ActiveX 控制嚮導](../mfc/reference/mfc-activex-control-wizard.md)啟動專案。

1. 右鍵單擊控件的介面節點。

   這將打開快捷功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

1. 從**屬性名稱**下拉清單中選擇其中一個條目。 例如,您可以選擇 **「文字**」 。

   由於**Text**是一個股票屬性,因此已**檢查 可綁定**屬性和**請求屬性**。

1. 從**IDL 屬性**選項卡中選擇以下複選框:**顯示綁定**和**預設綁定**,以將屬性添加到專案的屬性定義中的屬性定義。IDL 檔。 這些屬性使控制項對使用者可見,並使 stock 屬性成為預設的可綁定屬性。

此時,控件可以顯示數據源中的數據,但使用者將無法更新數據欄位。 如果希望控制項也能更新資料,請更改`OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函數,如下所示:

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

您現在可以生成專案,該專案將註冊控制項。 在對話框中插入控制項時,將添加 **「資料欄位**」和 **「資料來源」** 屬性,現在可以選擇要在控制項中顯示的資料來源和欄位。

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>建立可結合取得/集方法

除了資料繫結 get/set 方法外,您還可以建立[可綁定的股票屬性](#vchowcreatingbindablestockproperty)。

> [!NOTE]
> 此過程假定您有一個 ActiveX 控件專案,該專案將 Windows 控件子類。

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>使用新增屬性精靈新增可綁定 get/set 方法

1. 載入控制項專案。

1. 在 **「控制件設定」** 頁上,為控制項選擇要子類的視窗類。 例如,您可能希望對 EDIT 控制件進行子類。

1. 載入控制項專案。

1. 右鍵單擊控件的介面節點。

   這將打開快捷功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

1. 在 **「屬性名稱」** 框中鍵入屬性名稱。 用於`MyProp`此示例。

1. 從 **「屬性類型**」 下拉清單框中選擇數據類型。 此示例使用**短。**

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 從 IDL 屬性選項卡中選擇以下複選框:**可綁定**,**請求,****顯示繫結**與**預設的系統**的屬性定義的屬性定義。IDL 檔。 這些屬性使控制項對使用者可見,並使 stock 屬性成為預設的可綁定屬性。

1. 按一下 [完成] 。

1. 變更函數的`SetMyProp`正文,以便它包含以下代碼:

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. 傳遞給`BoundPropertyChanged``BoundPropertyRequestEdit`和 函數的參數是 屬性的"不pid",該屬性是傳遞給 中屬性的 id() 屬性的參數。IDL 檔。

1. 修改[OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函數,以便它包含以下代碼:

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. 變更函數`OnDraw`,以便它包含以下代碼:

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. 到標頭檔的公共部分,控制項類別的標頭檔,為成員變數添加以下定義(建構函數):

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. 使以下行成為函數中的最後一`DoPropExchange`行:

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. 變更函數`OnResetState`,以便它包含以下代碼:

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. 變更函數`GetMyProp`,以便它包含以下代碼:

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

您現在可以生成專案,該專案將註冊控制項。 在對話框中插入控制項時,將添加 **「資料欄位**」和 **「資料來源」** 屬性,現在可以選擇要在控制項中顯示的資料來源和欄位。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
