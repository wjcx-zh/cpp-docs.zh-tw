---
title: MFC ActiveX 控制項：加入自訂屬性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: af1ca2d63abcb112bfe1e7d7538dbf70fb817ae5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503875"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控制項：加入自訂屬性

自訂屬性與內建屬性不同之處在于該自訂屬性尚未由類別所執行 `COleControl` 。 自訂屬性是用來將 ActiveX 控制項的特定狀態或外觀公開給程式設計人員使用控制項。

本文說明如何使用 [加入屬性] Wizard 將自訂屬性新增至 ActiveX 控制項，並說明產生的程式碼修改。 主題包括：

- [使用新增屬性 Wizard 加入自訂屬性](#_core_using_classwizard_to_add_a_custom_property)

- [新增自訂屬性的屬性 Wizard 變更](#_core_classwizard_changes_for_custom_properties)

自訂屬性有四種不同的實作為：成員變數、具有通知的成員變數、Get/Set 方法，以及參數化。

- 成員變數執行

   這個實作為控制項類別中的成員變數來表示屬性的狀態。 當屬性值變更時不重要時，請使用成員變數執行。 在這三種類型中，此實值會建立最少的屬性支援程式碼。 成員變數執行的分派對應專案宏是 [DISP_PROPERTY](reference/dispatch-maps.md#disp_property)。

- 具有通知執行的成員變數

   此實作為包含成員變數，以及由 [加入屬性] Wizard 建立的通知函數。 架構會在屬性值變更之後，自動呼叫通知函數。 當您需要在屬性值變更時收到通知時，請使用成員變數搭配通知執行。 這種執行需要更多時間，因為它需要函式呼叫。 這項實行的分派對應專案宏是 [DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify)。

- 取得/設定方法執行

   此實作為由控制項類別中的一對成員函式所組成。 當控制項的使用者要求屬性的目前值，以及控制項的使用者要求屬性變更時，Get/Set 方法的執行會自動呼叫 Get 成員函式。 當您需要在執行時間計算屬性的值時，請使用這個實值，驗證控制項使用者在變更實際屬性之前所傳遞的值，或執行唯讀屬性類型。 這項實行的分派對應專案宏是 [DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex)。 下一節 [使用 [加入屬性] Wizard 加入自訂屬性](#_core_using_classwizard_to_add_a_custom_property)時，會使用 CircleOffset 自訂屬性來示範這項執行。

- 參數化的實作為

   [加入屬性] Wizard 支援參數化的執行。 參數化屬性 (有時也稱為屬性陣列) 可用來透過控制項的單一屬性來存取一組值。 這項實行的分派對應專案宏是 DISP_PROPERTY_PARAM。 如需有關如何執行這種類型的詳細資訊，請參閱 ActiveX 控制項： Advanced 主題一文中的實 [作為參數化屬性](mfc-activex-controls-advanced-topics.md) 。

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a> 使用新增屬性 Wizard 加入自訂屬性

下列程式示範如何加入自訂屬性 CircleOffset，它會使用 Get/Set 方法執行。 CircleOffset 自訂屬性可讓控制項的使用者從控制項周框矩形的中央位移圓圈。 以 Get/Set 方法以外的執行加入自訂屬性的程式非常類似。

這個相同的程式也可以用來新增您想要的其他自訂屬性。 以您的自訂屬性名稱取代 CircleOffset 屬性名稱和參數。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>使用新增屬性 Wizard 新增 CircleOffset 自訂屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入屬性**]。

   這會開啟 [ [加入屬性] Wizard](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)。

1. 在 [ **屬性名稱** ] 方塊中，輸入 *CircleOffset*。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 在 [ **屬性類型** ] 方塊中，選取 **`short`** 。

1. 輸入 Get 和 Set 函數的唯一名稱，或接受預設名稱。

1. 按一下 [完成] 。

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a> 新增自訂屬性的屬性 Wizard 變更

當您加入 CircleOffset 自訂屬性時，[加入屬性] Wizard 會變更標頭 (。H) 和執行 (。Control 類別的 CPP) 檔案。

將下列程式程式碼新增至。H 檔案，用來宣告兩個稱為 `GetCircleOffset` 和的函式 `SetCircleOffset` ：

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

下一行會加入至您的控制項。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

這一行會將特定識別碼指派給 CircleOffset 屬性，並從 [加入屬性] Wizard 的 [方法和屬性] 清單中的方法位置取得該號碼。

此外，下列程式程式碼新增至分派對應 (的。Control 類別的 CPP 檔) 將 CircleOffset 屬性對應到控制項的兩個處理常式函數：

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

最後，和函式的實， `GetCircleOffset` `SetCircleOffset` 會加入至控制項的結尾。.CPP 檔案。 在大多數情況下，您將修改 Get 函式以傳回屬性的值。 Set 函數通常會包含應該在屬性變更之前或之後執行的程式碼。

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

請注意，[加入屬性] Wizard 會自動將呼叫新增至 Set 函數的主體，以 [SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag)。 呼叫此函式會將控制項標示為已修改。 如果控制項已被修改，則在儲存容器時，將會儲存其新狀態。 每當屬性（儲存為控制項的持續性狀態的一部分）變更值時，就應該呼叫此函式。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 類別](reference/colecontrol-class.md)
