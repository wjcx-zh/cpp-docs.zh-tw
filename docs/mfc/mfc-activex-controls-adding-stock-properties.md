---
title: MFC ActiveX 控制項： 加入內建屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c51a2efba3c89b4e216fec96459b14c3d0c637d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357555"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控制項：加入內建屬性
內建屬性與不同的自訂屬性的類別已實作`COleControl`。 `COleControl` 包含控制項支援通用屬性的預先定義的成員函式。 某些常見的內容包含控制項的標題和前景和背景色彩。 如需其他內建屬性的資訊，請參閱[加入屬性精靈 所支援的內建屬性](#_core_stock_properties_supported_by_classwizard)本文稍後。 內建屬性的分派對應項目一律都會加**DISP_STOCKPROP**。  
  
 這篇文章描述如何將 ActiveX 控制項，使用 [加入屬性精靈] （在此情況下，標題） 的內建屬性，並說明修改之產生的程式碼。 主題包括：  
  
-   [使用 [加入屬性精靈] 將內建屬性](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [加入屬性精靈 變更為內建屬性](#_core_classwizard_changes_for_stock_properties)  
  
-   [加入屬性精靈 所支援的內建屬性](#_core_stock_properties_supported_by_classwizard)  
  
-   [內建屬性和通知](#_core_stock_properties_and_notification)  
  
-   [色彩屬性](#_core_color_properties)  
  
    > [!NOTE]
    >  Visual Basic 自訂控制項通常會有屬性，例如頂端、 左邊、 寬度、 高度、 對齊、 標記、 名稱、 定位點索引、 定位點和父代。 ActiveX 控制項容器，不過，必須負責實作這些控制項的屬性，因此 ActiveX 控制項應該支援這些屬性。  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用加入屬性精靈來加入內建屬性  
 加入內建屬性需要較少的程式碼加入自訂屬性，因為超過支援的屬性會自動處理`COleControl`。 下列程序示範如何將庫存標題屬性加入至 ActiveX 控制項架構，也可用來新增其他內建屬性。 替代的所選的內建屬性名稱的標題。  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要加入內建的標題屬性使用 加入屬性精靈  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
     這會開啟[加入屬性精靈](../ide/names-add-property-wizard.md)。  
  
5.  在**屬性名稱**方塊中，按一下**標題**。  
  
6.  按一下 [ **完成**]。  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> 加入屬性精靈變更為內建屬性  
 因為`COleControl`支援內建屬性，加入屬性精靈 不會變更以任何方式在類別宣告，將屬性新增至分派對應。 加入屬性精靈 會將下列這一行加入控制項，在實作中的分派對應 (。CPP) 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 下列這一行加入至控制項的介面描述 (。IDL) 檔：  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 這一行標題屬性指派特定的識別碼。 請注意，此屬性是可繫結，並從資料庫將要求的權限才能修改值。  
  
 這讓標題屬性使用控制項的使用者。 若要使用的內建屬性的值，存取成員變數或成員函式`COleControl`基底類別。 如需有關這些成員變數和成員函式的詳細資訊，請參閱下節中，加入屬性精靈 所支援的內建屬性。  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> 內建支援的屬性加入屬性精靈  
 `COleControl`類別提供九個內建屬性。 您可以新增您要使用 [加入屬性精靈] 的屬性。  
  
|屬性|分派對應項目|如何存取值|  
|--------------|------------------------|-------------------------|  
|**外觀**|**DISP_STOCKPROP_APPEARANCE （)**|值可做為存取**m_sAppearance**。|  
|`BackColor`|**DISP_STOCKPROP_BACKCOLOR （)**|值，藉由呼叫可存取`GetBackColor`。|  
|`BorderStyle`|**DISP_STOCKPROP_BORDERSTYLE （)**|值可做為存取**m_sBorderStyle**。|  
|**標題**|**DISP_STOCKPROP_CAPTION （)**|值，藉由呼叫可存取`InternalGetText`。|  
|**已啟用**|**DISP_STOCKPROP_ENABLED （)**|值可做為存取**m_bEnabled**。|  
|**字型**|**DISP_STOCKPROP_FONT （)**|請參閱文章[MFC ActiveX 控制項： 使用字型](../mfc/mfc-activex-controls-using-fonts.md)使用量。|  
|`ForeColor`|**DISP_STOCKPROP_FORECOLOR （)**|值，藉由呼叫可存取`GetForeColor`。|  
|**hWnd**|**DISP_STOCKPROP_HWND （)**|值可做為存取`m_hWnd`。|  
|**Text**|**DISP_STOCKPROP_TEXT （)**|值，藉由呼叫可存取`InternalGetText`。 這個屬性等同於**標題**，除了屬性名稱。|  
|**ReadyState**|**DISP_STOCKPROP_READYSTATE()**|值那樣 m_lReadyState 或 `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> 內建屬性和通知  
 大部分的內建屬性都可以覆寫的通知函式。 例如，每當`BackColor`屬性變更，`OnBackColorChanged`呼叫函式 （控制項類別的成員函式）。 預設實作 (在`COleControl`) 呼叫`InvalidateControl`。 如果您想要採取其他動作以回應此情況下，請覆寫這個函式。  
  
##  <a name="_core_color_properties"></a> 色彩屬性  
 您可以使用內建`ForeColor`和`BackColor`屬性或您自己的自訂色彩屬性，繪製控制項時。 若要使用的色彩屬性，呼叫[COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor)成員函式。 此函式的參數是色彩屬性和選用的調色盤控制代碼的值。 傳回值是**COLORREF**值，可以傳遞至 GDI 函式，例如`SetTextColor`和`CreateSolidBrush`。  
  
 內建的色彩值`ForeColor`和`BackColor`內容的存取方式呼叫`GetForeColor`或`GetBackColor`分別函式。  
  
 下列範例示範如何使用這些兩個色彩屬性，繪製控制項時。 它會初始化暫存**COLORREF**變數和`CBrush`物件呼叫`TranslateColor`： 一個使用`ForeColor`屬性和其他使用`BackColor`屬性。 暫存`CBrush`物件會被用來繪製控制項的矩形，並使用設定的文字色彩`ForeColor`屬性。  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 屬性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 類別](../mfc/reference/colecontrol-class.md)
