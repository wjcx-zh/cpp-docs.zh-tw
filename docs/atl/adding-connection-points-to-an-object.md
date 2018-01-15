---
title: "將連接點加入物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f63ec5bd9029302192e640e42a3d012df347219d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-connection-points-to-an-object"></a>將連接點加入物件
[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)示範如何建立具有連接點支援的控制項、 如何加入事件，以及如何實作連接點。 ATL 實作連接點與[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)類別。  
  
 若要實作連接點，您有兩個選擇：  
  
-   實作您自己外寄的事件來源，將連接點加入至控制項或物件。  
  
-   重複使用另一個類型程式庫中定義的連接點介面。  
  
 在任一情況下，實作連接點精靈會使用型別程式庫來執行其工作。  
  
### <a name="to-add-a-connection-point-to-a-control-or-object"></a>若要加入的控制項或物件的連接點  
  
1.  .Idl 檔案的程式庫區塊中定義的分配介面。 如果您使用 ATL 控制項精靈 」 建立控制項時，您就會啟用連接點的支援，將已建立的分配介面。 如果您未啟用的連接點支援您在建立控制項時，您必須手動加入 dispinterface.idl 檔案。 以下是分配介面的範例。 外寄的介面並不一定要分派介面，但許多指令碼語言，例如 VBScript 和 JScript 需要，因此這個範例會使用兩種分配介面：  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]  
  
     使用 uuidgen.exe 或 guidgen.exe 公用程式產生的 GUID。  
  
2.  加入做為 dispinterface`[default,source]`介面的 coclass 專案的.idl 檔中的物件中。 同樣地，如果您在建立控制項時，您就會啟用連接點的支援，ATL 控制項精靈將會建立`[default,source`] 項目。 若要手動新增此項目，加入線條以粗體顯示：  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]  
  
     請參閱中的.idl 檔案[Circ](../visual-cpp-samples.md) ATL 範例的範例。  
  
3.  使用類別檢視，來將方法和屬性加入至事件介面。 以滑鼠右鍵按一下 類別檢視中的類別，並指向**新增**捷徑功能表，然後按一下 **加入連接點**。  
  
4.  在**來源介面**實作連接點精靈中，選取清單方塊**專案介面**。 如果您選擇您的控制項和按介面**確定**，您將會：  
  
    -   產生與實作的程式碼，將會發出連出呼叫事件的事件 proxy 類別的標頭檔。  
  
    -   加入連接點對應的項目。  
  
     您也會看到您的電腦上的所有型別程式庫的清單。 您只應該使用這些其他類型程式庫的其中一個定義您的連接點，如果您想要實作完全相同的輸出介面另一個類型程式庫中找到。  
  
### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>若要重複使用的連接點介面定義中另一個類型程式庫  
  
1.  在 類別檢視，以滑鼠右鍵按一下類別可實作**BEGIN_COM_MAP**巨集，指向**新增**捷徑功能表，然後按一下 **加入連接點**。  
  
2.  在實作連接點精靈中，選取型別程式庫和介面類型程式庫中，按一下 **新增**。  
  
3.  編輯.idl 檔案為：  
  
    -   Dispinterface 複製正在使用其事件來源物件的.idl 檔案。  
  
    -   使用**importlib**該型別程式庫的指示。  
  
## <a name="see-also"></a>請參閱  
 [連接點](../atl/atl-connection-points.md)

