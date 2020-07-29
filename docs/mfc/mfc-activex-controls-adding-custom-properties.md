---
title: MFC ActiveX 控制項：加入自訂屬性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 805fffcc6cafe92df91af6b01bb53240a0d70f51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230489"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控制項：加入自訂屬性

自訂屬性與內建屬性不同之處在于，自訂屬性尚未由 `COleControl` 類別執行。 自訂屬性是用來將 ActiveX 控制項的特定狀態或外觀公開給使用控制項的程式設計人員。

本文說明如何使用 [加入屬性] Wizard 將自訂屬性新增至 ActiveX 控制項，並說明產生的程式碼修改。 主題包括：

- [使用 [新增屬性] Wizard 來新增自訂屬性](#_core_using_classwizard_to_add_a_custom_property)

- [新增自訂屬性的屬性 Wizard 變更](#_core_classwizard_changes_for_custom_properties)

自訂屬性有四種不同的實作為：成員變數、具有通知的成員變數、Get/Set 方法，以及參數化。

- 成員變數的執行

   這個實作為控制項類別中的成員變數，表示屬性的狀態。 當屬性值變更時，請使用成員變數實作為不重要的方式。 在這三種類型中，此執行會為屬性建立最少量的支援程式碼。 成員變數實現的分派對應專案宏是[DISP_PROPERTY](reference/dispatch-maps.md#disp_property)。

- 具有通知執行的成員變數

   此實作為由 [加入屬性] Wizard 建立的成員變數和通知函數所組成。 在屬性值變更之後，架構會自動呼叫通知函式。 當您需要在屬性值變更之後收到通知時，請使用成員變數搭配通知執行。 此執行需要更多時間，因為它需要函式呼叫。 此執行的分派對應專案宏為[DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify)。

- 取得/設定方法執行

   這個實作用是由控制項類別中的一對成員函式所組成。 當控制項的使用者要求屬性的目前值，以及當控制項的使用者要求屬性變更時，Get/Set 方法會自動呼叫 Get 成員函式。 當您需要在執行時間計算屬性的值、在變更實際屬性之前驗證控制項的使用者所傳遞的值，或執行唯讀或僅限寫入的屬性類型時，請使用此執行。 此執行的分派對應專案宏為[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex)。 下一節[使用 [加入屬性] Wizard 加入自訂屬性](#_core_using_classwizard_to_add_a_custom_property)時，會使用 CircleOffset 自訂屬性來示範這項執行。

- 參數化實

   [加入屬性] Wizard 支援參數化的執行。 參數化屬性（有時稱為屬性陣列）可以透過控制項的單一屬性來存取一組值。 此執行的分派對應專案宏為 DISP_PROPERTY_PARAM。 如需有關如何執行此類型的詳細資訊，請參閱 ActiveX 控制項： Advanced 主題文章中的[執行參數化屬性](mfc-activex-controls-advanced-topics.md)。

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>使用 [新增屬性] Wizard 來新增自訂屬性

下列程式示範如何加入自訂屬性 CircleOffset，它會使用 Get/Set 方法實作為。 CircleOffset 自訂屬性可讓控制項的使用者從控制項的周框矩形中央位移圓形。 以 Get/Set 方法以外的實作為加入自訂屬性的程式非常類似。

這個相同的程式也可以用來新增您想要的其他自訂屬性。 以您的自訂屬性名稱取代 CircleOffset 屬性名稱和參數。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>使用新增屬性 Wizard 新增 CircleOffset 自訂屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

   這會開啟 [[新增屬性] Wizard](../ide/names-add-property-wizard.md)。

1. 在 [**屬性名稱**] 方塊中，輸入*CircleOffset*。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 在 [**屬性類型**] 方塊中，選取 **`short`** 。

1. 輸入您的 Get 和 Set 函數的唯一名稱，或接受預設名稱。

1. 按一下 [完成] 。

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>新增自訂屬性的屬性 Wizard 變更

當您新增 CircleOffset 自訂屬性時，[新增屬性] Wizard 會對標頭（進行變更。H）和實（。CPP）檔案。

下列幾行會加入至。H 檔案來宣告兩個名為 `GetCircleOffset` 和的函式 `SetCircleOffset` ：

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

下面這一行會加入至控制項的。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

這一行會指派特定識別碼的 CircleOffset 屬性，從 [加入屬性] Wizard 的方法和屬性清單中的方法位置取得。

此外，下列這一行會加入至分派對應（在中）。控制項類別的 CPP 檔案），以將 CircleOffset 屬性對應至控制項的兩個處理函式：

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

最後，和函式的 `GetCircleOffset` 實 `SetCircleOffset` 作用會加入至控制項的結尾。CPP 檔案。 在大部分的情況下，您將修改 Get 函式以傳回屬性的值。 Set 函式通常會包含應該在屬性變更之前或之後執行的程式碼。

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

請注意，[加入屬性] Wizard 會自動將呼叫（ [SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag)）新增至集合函數的主體。 呼叫這個函式會將控制項標示為已修改。 如果控制項已修改，則儲存容器時，將會儲存其新狀態。 每當屬性（儲存為控制項的持續性狀態的一部分）變更值時，就應該呼叫這個函數。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 類別](reference/colecontrol-class.md)
