---
title: MFC ActiveX 控制項： 加入自訂屬性 |Microsoft 文件
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
ms.openlocfilehash: fc3aa3f7aa8b6f4abf28c12a11f75540f59238e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控制項：加入自訂屬性
自訂屬性與不同的內建屬性的自訂屬性不已實作的`COleControl`類別。 自訂屬性用來公開某些狀態或 ActiveX 控制項，以程式設計人員使用控制項的外觀。  
  
 這篇文章描述如何將自訂屬性加入至 ActiveX 控制項，使用 [加入屬性精靈]，並說明修改之產生的程式碼。 主題包括：  
  
-   [使用 [加入屬性精靈] 來新增自訂內容](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [加入屬性精靈 變更為自訂屬性](#_core_classwizard_changes_for_custom_properties)  
  
 自訂屬性有四種實作： 成員變數，其中包含通知 Get/Set 方法，使用參數化變數成員。  
  
-   成員變數的實作  
  
     此實作中的控制項類別的成員變數以表示屬性的狀態。 不一定要知道當屬性值變更時，請使用成員變數的實作。 三種類型，此實作會建立最少的屬性支援程式碼。 分派對應項目巨集的成員變數的實作是[DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property)。  
  
-   與通知實作的成員變數  
  
     這個實作是由成員變數，以及加入屬性精靈所建立的告知函式所組成。 屬性值變更之後，會自動通知函式呼叫由架構。 成員變數與通知實作需要時使用通知之後已變更屬性值。 這個實作需要更多時間，因為它需要函式呼叫。 分派對應項目巨集，此實作是[DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify)。  
  
-   Get/Set 方法的實作  
  
     這個實作是由一對成員函式位於控制項類別所組成。 Get/Set 方法實作自動取得成員函式，當控制項的使用者要求此屬性的目前值和集合成員函式時呼叫控制項的使用者要求變更的屬性。 當您需要執行階段計算屬性的值驗證之前變更實際的內容中，控制項的使用者所傳遞的值或實作讀取-或唯寫屬性類型，請使用這項實作。 分派對應項目巨集，此實作是[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)。 下一節，[使用 [加入屬性精靈] 來新增自訂內容](#_core_using_classwizard_to_add_a_custom_property)，以示範這項實作會使用 CircleOffset 自訂屬性。  
  
-   參數化的實作  
  
     加入屬性精靈 支援參數化的實作。 （有時稱為屬性陣列） 的參數化的屬性可以用來透過控制項的單一屬性來存取一組值。 分派對應項目巨集，此實作是`DISP_PROPERTY_PARAM`。 如需實作此類型的詳細資訊，請參閱[實作參數化屬性](../mfc/mfc-activex-controls-advanced-topics.md)文章 ActiveX 控制項： 進階主題。  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> 使用加入屬性精靈來加入自訂屬性  
 下列程序示範如何將自訂屬性，CircleOffset，使用 Get/Set 方法的實作。 CircleOffset 自訂屬性可讓控制項的使用者，來彌補中央的控制項的週框圓形。 將非 Get/Set 方法的實作的自訂屬性的程序是非常類似。  
  
 這個相同的程序也可用來新增其他您想要的自訂屬性。 替換成您的自訂屬性名稱 CircleOffset 屬性名稱和參數。  
  
#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>若要加入使用 [加入屬性精靈] 的 CircleOffset 自訂屬性  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
     這會開啟[加入屬性精靈](../ide/names-add-property-wizard.md)。  
  
5.  在**屬性名稱**方塊中，輸入`CircleOffset`。  
  
6.  在 [實作類型] 中，按一下 [Get/Set 方法] 。  
  
7.  在**屬性型別**方塊中，選取**簡短**。  
  
8.  輸入為 Get 和 Set 函式的唯一名稱，或接受預設名稱。  
  
9. 按一下 [ **完成**]。  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a> 加入屬性精靈變更自訂屬性  
 當您新增 CircleOffset 自訂屬性時，加入屬性精靈 會變更標頭檔 (。H） 和實作 (。控制項類別 CPP) 檔案。  
  
 加入下列幾行。若要宣告兩個函式呼叫 H 檔案`GetCircleOffset`和`SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 下列這一行加入到您的控制項。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 這一行 CircleOffset 屬性指派特定的 ID 編號，取自方法和屬性清單中的 [加入屬性精靈] 的方法的位置。  
  
 此外，下列這一行加入到分派對應 (在中。控制項類別 CPP 檔案） 來將 CircleOffset 屬性對應至控制項的兩個處理常式函式：  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 最後，實作`GetCircleOffset`和`SetCircleOffset`函數會加入至控制項的結尾。CPP 檔案。 在大部分情況下，您將修改 Get 函式來傳回屬性的值。 Set 函式通常會包含之前或在屬性變更後應該執行的程式碼。  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 請注意，[加入屬性精靈] 會自動將呼叫，為[SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)，Set 函式的主體。 呼叫此函式會將控制項的標記，為已修改。 如果控制項已被修改，則在儲存容器時，將會儲存成新的狀態。 屬性，儲存為部分控制項的永續性狀態，變更值時，應該呼叫此函式。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 屬性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 類別](../mfc/reference/colecontrol-class.md)
