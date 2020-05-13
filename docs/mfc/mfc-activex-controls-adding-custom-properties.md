---
title: MFC ActiveX 控制項：加入自訂屬性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 00f7a879582bca562ce626fe224206094fd19bc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364694"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控制項：加入自訂屬性

自定義屬性與股票屬性不同,因為類尚未實現`COleControl`自定義屬性。 自定義屬性用於向使用 該控制項的程式師公開 ActiveX 控制件的特定狀態或外觀。

本文介紹如何使用"添加屬性嚮導"向 ActiveX 控制件添加自定義屬性,並解釋生成的代碼修改。 主題包括：

- [使用「新增屬性精靈」新增自訂屬性](#_core_using_classwizard_to_add_a_custom_property)

- [為自訂屬性加入屬性精靈變更](#_core_classwizard_changes_for_custom_properties)

自定義屬性有四種實現類型:成員變數、帶有通知的成員變數、獲取/設置方法和參數化。

- 成員變數實現

   此實現表示屬性的狀態作為控件類中的成員變數。 當不知道屬性值何時更改並不重要時,請使用成員變數實現。 在三種類型中,此實現為屬性創建的支持代碼最少。 成員變數實現的調度映射條目宏[DISP_PROPERTY。](../mfc/reference/dispatch-maps.md#disp_property)

- 具通知實作的成員變數

   此實現由成員變數和由添加屬性嚮導創建的通知函數組成。 屬性值更改後,框架會自動調用通知函數。 在屬性值更改後需要通知時,將「成員變數」與通知實現一起使用。 此實現需要更多時間,因為它需要函數調用。 此實現的排程對應項目巨集[DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify)。

- 取得/設定方法

   此實現由控制類中的一對成員函數組成。 當控件的使用者請求屬性的當前值和"設置成員"函數時,當控件的使用者請求更改該屬性時,"獲取/設置方法"實現會自動調用 Get 成員函數。 當您需要在運行時計算屬性的值、在更改實際屬性之前驗證控制件使用者傳遞的值或實現唯讀或只寫屬性類型時,請使用此實現。 此實作的排程對應的資料巨集[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)。 以下部分使用[添加屬性嚮導添加自定義屬性](#_core_using_classwizard_to_add_a_custom_property)「使用 CircleOffset 自訂屬性來演示此實現。

- 參數化實現

   添加屬性嚮導支援參數化實現。 參數化屬性(有時稱為屬性陣列)可用於通過控制項的單個屬性存取一組值。 此實現的調度映射條目宏DISP_PROPERTY_PARAM。 有關實現此類型的詳細資訊,請參閱在「ActiveX 控制件:進階主題」一文中[實現參數化屬性](../mfc/mfc-activex-controls-advanced-topics.md)。

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>使用「新增屬性精靈」新增自訂屬性

以下過程演示了添加自定義屬性 CircleOffset,它使用獲取/設置方法實現。 CircleOffset 自定義屬性允許控制項的使用者從控制項的邊界矩形的中心偏移圓。 使用獲取/設置方法以外的實現添加自定義屬性的過程非常相似。

此過程還可用於添加所需的其他自定義屬性。 將自訂屬性名稱替換為 CircleOffset 屬性名稱和參數。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>使用「新增屬性精靈」新增「圈位移」自訂屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

   這會開啟[新增屬性精靈](../ide/names-add-property-wizard.md)。

1. 在**屬性名稱**框中,鍵入 *「圓偏移*」。。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 在 **「屬性類型」** 框中,選擇 **「短**」。。

1. 為獲取和設置函數鍵入唯一名稱,或接受預設名稱。

1. 按一下 [完成] 。

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>為自訂屬性加入屬性精靈變更

添加"圈偏移"自定義屬性時,"添加屬性嚮導"會更改標頭 (。H) 和實現 (.控制類的 CPP)檔。

以下行將新增到 。H 檔宣告兩個函`GetCircleOffset`數`SetCircleOffset`, 稱為與 :

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

以下行將新增到控制項的 。IDL 檔案:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

此行為 CircleOffset 屬性分配一個特定的 ID 號,該 ID 號取自該方法在添加屬性嚮導的方法和屬性清單中的位置。

此外,以下行將添加到調度映射(在中)。控制項類別的 CPP 檔)將 CircleOffset 屬性映射到控制項的兩個處理程式函數:

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

最後,將`GetCircleOffset`和`SetCircleOffset`函數的實現添加到控制項的末尾。CPP 檔。 在大多數情況下,您將修改 Get 函數以返回屬性的值。 Set 函數通常包含應在屬性更改之前或之後執行的代碼。

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

請注意,添加屬性嚮導會自動將呼叫設定[修改Flag'](../mfc/reference/colecontrol-class.md#setmodifiedflag)添加到Set函數的正文中。 調用此函數將控件標記為已修改。 如果控件已被修改,則在保存容器時將保存其新狀態。 每當作為控制項持久狀態的一部分保存的屬性更改值時,都應調用此函數。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)
