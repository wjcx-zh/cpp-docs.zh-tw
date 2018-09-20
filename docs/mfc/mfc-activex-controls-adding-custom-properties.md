---
title: MFC ActiveX 控制項： 加入自訂屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98cf8a0532c3b1f2044ba0338d3f2f2bf8e73813
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390980"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控制項：加入自訂屬性

自訂屬性與不同的內建屬性的自訂屬性尚未已實作的`COleControl`類別。 自訂屬性用來公開 （expose） 的特定狀態或 ActiveX 控制項的程式設計人員使用控制項的外觀。

這篇文章描述如何將自訂屬性加入至 ActiveX 控制項，使用 [新增屬性精靈]，並說明產生的程式碼修改。 主題包括：

- [使用 [新增屬性精靈] 來新增自訂屬性](#_core_using_classwizard_to_add_a_custom_property)

- [加入自訂屬性的屬性精靈變更](#_core_classwizard_changes_for_custom_properties)

自訂屬性可分成四個不同的實作： 成員變數、 通知、 Get/Set 方法，與使用參數化變數成員。

- 成員變數的實作

     這項實作以控制項類別中的成員變數，表示此屬性的狀態。 當您不一定要知道當屬性值變更時，請使用成員變數的實作。 三種類型，此實作會建立最少的支援屬性的程式碼。 分派對應項目巨集的成員變數的實作就[DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property)。

- 與通知實作的成員變數

     此實作是由成員變數，以及加入屬性精靈所建立的通知函式所組成。 通知函式會自動由架構呼叫的屬性值變更之後。 使用成員變數通知實作時您需要的屬性值變更後收到通知。 此實作會需要更多時間，因為它需要函式呼叫。 分派對應項目巨集，此實作就[DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify)。

- 取得或設定方法的實作

     此實作是由一組控制項類別中的成員函式所組成。 Get/Set 方法實作會自動呼叫 Get 成員函式控制項的使用者要求此屬性的目前值時，Set 成員函式控制項的使用者要求變更的屬性時。 當您需要在執行期間，計算屬性的值驗證控制項的使用者才能變更實際的屬性，傳遞的值或實作讀取-或唯寫的屬性型別，請使用這項實作。 分派對應項目巨集，此實作就[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)。 下一節[使用 [新增屬性精靈] 來新增自訂屬性](#_core_using_classwizard_to_add_a_custom_property)，來示範這項實作會使用 CircleOffset 自訂屬性。

- 參數化的實作

     加入屬性精靈 支援參數化的實作。 參數化的屬性 （有時稱為屬性的陣列） 可用來透過您控制項的單一屬性來存取一組值。 分派對應項目巨集，此實作是 DISP_PROPERTY_PARAM。 如需有關如何實作這種類型的詳細資訊，請參閱 <<c0> [ 實作參數化屬性](../mfc/mfc-activex-controls-advanced-topics.md)文中所 ActiveX 控制項： 進階主題。

##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> 使用加入屬性精靈來加入自訂屬性

下列程序示範如何將自訂屬性，CircleOffset，使用 Get/Set 方法的實作。 CircleOffset 自訂屬性可讓控制項的使用者從控制項的週框矩形的中心圓的位移。 新增非 Get/Set 方法的實作的自訂屬性的程序是非常類似。

這個相同的程序也可用來新增其他您想要的自訂屬性。 替換成您的自訂屬性名稱 CircleOffset 屬性名稱和參數。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>若要加入使用 加入屬性精靈 CircleOffset 自訂屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

     這會開啟[加入屬性精靈](../ide/names-add-property-wizard.md)。

1. 在 **屬性名稱**方塊中，輸入*CircleOffset*。

1. 在 [實作類型] 中，按一下 [Get/Set 方法] 。

1. 在 **屬性的型別**方塊中，選取**簡短**。

1. 輸入為 Get 和 Set 函式的唯一名稱，或接受預設名稱。

9. 按一下 [ **完成**]。

##  <a name="_core_classwizard_changes_for_custom_properties"></a> 加入屬性精靈變更自訂屬性

當您新增 CircleOffset 自訂屬性時，加入屬性精靈 會變更標頭檔 (。H） 和實作 (。控制項類別的 CPP) 檔案。

加入下列幾行。H 檔案中宣告兩個呼叫的函式`GetCircleOffset`和`SetCircleOffset`:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

下面這一行加入至您的控制項。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

這一行會將資料區間指派 CircleOffset 屬性特定的 ID 編號，取自方法和屬性清單中的 [新增屬性精靈] 的方法的位置。

此外下, 面這一行加入分派對應 (在中。控制項類別的 CPP 檔案） 的 CircleOffset 屬性對應至控制項的兩個處理常式函式：

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

最後，實作`GetCircleOffset`和`SetCircleOffset`函數會加入至控制項的結尾。CPP 檔案。 在大部分情況下，您將修改 Get 函式來傳回屬性的值。 Set 函式通常會包含之前或之後的屬性變更應該執行的程式碼。

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

請注意，加入屬性精靈 會自動將呼叫中，加入[SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)，Set 函式的主體。 呼叫此函式會將控制項標示為已修改。 如果控制項已被修改，則在儲存容器時，將會儲存成新的狀態。 每當另存為控制項的永續性狀態，一部分的屬性值變更時，應該呼叫此函式。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)
