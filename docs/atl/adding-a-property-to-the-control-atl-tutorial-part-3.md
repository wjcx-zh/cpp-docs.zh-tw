---
title: "將屬性加入至控制項 (ATL 教學課程，第 3 部分) |Microsoft 文件"
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
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a316ba56c551d0ee47261160058b00eca5e51a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>將屬性加入至控制項 (ATL 教學課程，第 3 部分)
`IPolyCtl`是包含控制項的自訂方法和屬性的介面，您會將屬性加入它。  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>若要加入屬性，使用 加入屬性精靈  
  
1.  在 類別檢視中，展開 多邊形分支。  
  
2.  以滑鼠右鍵按一下 IPolyCtl。  
  
3.  在捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
     加入屬性精靈 會出現。  
  
4.  在下拉式清單中的屬性類型，選取`SHORT`。  
  
5.  型別`Sides`為**屬性名稱。**  
  
6.  按一下**完成**完成 新增屬性。  
  
 當您新增屬性至介面時，MIDL （編譯.idl 檔案的程式） 會定義`Get`擷取其值的方法和`Put`設定新值的方法。 方法的命名方式是將`put_`和`get_`屬性名稱。  
  
 加入屬性精靈 會將必要的行加入至.idl 檔案。 它也會加入`Get`和`Put`函式原型中 PolyCtl.h 的類別定義，並將空白的實作加入至 PolyCtl.cpp。 您可以開啟 PolyCtl.cpp 並尋找函式檢查此`get_Sides`和`put_Sides`。  
  
 雖然您現在可以設定及擷取屬性的基本架構函式，它需要的儲存位置。 您將建立變數，以儲存屬性，並且據以更新函式。  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>若要建立一個變數來儲存屬性，並且更新 put 和 get 的方法  
  
1.  從 方案總管 中，開啟 PolyCtl.h 和之後的定義中加入下行`m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  設定的預設值`m_nSides`。 請將這一行加入建構函式中 PolyCtl.h 圖形三角形的預設值：  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  實作`Get`和`Put`方法。 `get_Sides`和`put_Sides`PolyCtl.h 已加入函式宣告。 取代為 PolyCtl.cpp 中的程式碼`get_Sides`和`put_Sides`為下列程式碼：  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides`方法會傳回目前的值`Sides`透過屬性`pVal`指標。 在`put_Sides`方法，該程式碼可確保使用者會設定`Sides`屬性設為可接受的值。 最小值必須是 2，而且因為將使用的點陣列，為每個邊，100 限制為最大值。  
  
 您現在有一個屬性呼叫`Sides`。 在下一個步驟中，您會變更繪圖程式碼使用它。  
  
 [步驟 2 至](../atl/adding-a-control-atl-tutorial-part-2.md)&#124;[至步驟 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)

