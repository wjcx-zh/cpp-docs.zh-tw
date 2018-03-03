---
title: "將在網頁上 (ATL 教學課程，第 7 部分) 控制項放入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 523086c70d9f974c014f5d33a71bf9309b8e017d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>將控制項放在網頁上 (ATL 教學課程，第 7 部分)
現在已完成您的控制項。 若要查看您在真實世界的情況下運作的控制項，請將它放在網頁上。 定義您的控制項時，已建立包含控制項的 HTML 檔。 開啟 PolyCtl.htm 檔案從**方案總管 中**，您可以看到您在網頁上的控制項。  
  
 在此步驟中，您將指令碼來回應事件的網頁。 您也會修改讓 Internet Explorer 就會知道控制項已安全用於指令碼控制項。  
  
## <a name="scripting-the-web-page"></a>指令碼處理網頁  
 控制項不會不進行任何作業，因此變更網頁回應您所傳送的事件。  
  
#### <a name="to-script-the-web-page"></a>若要編寫指令碼的 Web 網頁  
  
1.  開啟 PolyCtl.htm 並選取 [HTML] 檢視。 將下列行加入至 HTML 程式碼。 應該將它們加入之後`</OBJECT>`前`</BODY>`。  
  
 ```  
 
 <SCRIPT LANGUAGE="VBScript">  
 <!--  
    Sub PolyCtl_ClickIn(x, y)  
    PolyCtl.Sides = PolyCtl.Sides + 1  
    End Sub  
    Sub PolyCtl_ClickOut(x, y)  
    PolyCtl.Sides = PolyCtl.Sides - 1  
    End Sub  
 -->  
 </SCRIPT>  
 ```  
  
2.  儲存 HTM 檔。  
  
 您已加入一些 VBScript 程式碼，從控制項取得側邊屬性並增加一個的邊數，如果您在控制項內按一下。 如果您按一下控制之外，您會減少一個邊數。  
  
## <a name="indicating-that-the-control-is-safe-for-scripting"></a>指出控制項可安全用於指令碼  
 您可以在 Internet Explorer 檢視網頁的控制項，或為了方便起見，使用 Visual c + + 內建的 Web 瀏覽器檢視。 若要查看您的 Web 瀏覽器檢視中的控制項，以滑鼠右鍵按一下 PolyCtl.htm，，然後按一下**瀏覽器中的檢視**。  
  
 根據您目前的 Internet Explorer 安全性設定，您可能會收到安全性警告對話方塊中指出的控制項可能不安全要編寫指令碼，就可能損壞。 例如，如果您的控制項顯示檔案，但也有`Delete`刪除檔案的方法，則可放心將只在頁面上檢視。 將不安全的指令碼，不過，因為可能會有人呼叫`Delete`方法。  
  
> [!IMPORTANT]
>  此教學課程中，您可以變更您的安全性設定，在 Internet Explorer 中執行不標示為安全的 ActiveX 控制項。 在控制台中，按一下 **網際網路內容**按一下**安全性**變更適當的設定。 當您完成本教學課程之後時，變更您的安全性設定回其原始狀態。  
  
 您以程式設計的方式可以提醒 Internet Explorer，它不需要顯示安全性警示 對話方塊，針對這個特定的控制項。 您可以使用`IObjectSafety`介面和 ATL 提供類別中的此介面的實作[IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md)。 若要將介面加入至您的控制項，加入`IObjectSafetyImpl`至繼承類別的清單並加入其 COM 對應中的項目。  
  
#### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>若要將 IObjectSafetyImpl 加入控制項  
  
1.  中 PolyCtl.h 繼承的類別清單的結尾加入下列程式，並在上一行加入逗號：  
  
 [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  將下列行加入至 COM 中的對應 PolyCtl.h:  
  
 [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## <a name="building-and-testing-the-control"></a>建置和測試控制項  
 建置控制項。 在建置完成時，請再次在瀏覽器檢視中開啟 PolyCtl.htm。 此時，網頁上應該會顯示直接沒有安全性警告對話方塊。 按一下 多邊形; 內邊數增加一個。 按一下要減少的側邊的多邊形的外面。 如果您嘗試減少的側邊小於 3，您會看到您所設定的錯誤訊息。  
  
 [回到步驟 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="next-steps"></a>後續步驟  
 以上總結 ATL 教學課程。 如需連結 ATL 的詳細資訊，請參閱[ATL 起始頁](../atl/active-template-library-atl-concepts.md)。  
  
## <a name="see-also"></a>請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)

