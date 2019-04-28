---
title: 將連接點加入物件
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
ms.openlocfilehash: 7341e69852ed804122e0196b51d305f5af0c35b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223515"
---
# <a name="adding-connection-points-to-an-object"></a>將連接點加入物件

[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)示範如何建立連接點支援的控制項、 如何加入事件，以及如何實作連接點。 ATL 實作連接點[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)類別。

若要實作連接點，您會有兩個選擇：

- 實作您自己連出的事件來源，藉由將控制項或物件的連接點。

- 重複使用另一個類型程式庫中定義的連接點介面。

在任一情況下，實作連接點精靈會使用型別程式庫來執行其工作。

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>若要加入的控制項或物件的連接點

1. Dispinterface 在中定義的程式庫區塊的.idl 檔案。 如果您在使用 ATL 控制項精靈 建立控制項時，您就會啟用連接點的支援，將已建立的分配介面。 如果您在建立控制項時，您並未啟用連接點的支援，您必須以手動方式加入 dispinterface.idl 檔案。 以下是分配介面的範例。 外寄的介面並不一定要分派介面，但許多指令碼語言，例如 VBScript 和 JScript 需要這項目，因此這個範例會使用兩個的分配介面：

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   您可以使用 uuidgen.exe 或 guidgen.exe 公用程式來產生 GUID。

2. 新增為 dispinterface`[default,source]`中 coclass 的專案的.idl 檔案中的物件介面。 同樣地，如果您在建立控制項時，您就會啟用連接點的支援，ATL 控制項精靈將會建立`[default,source`] 項目。 若要手動新增此項目，請加入一行以粗體顯示：

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   請參閱中的.idl 檔案[Circ](../overview/visual-cpp-samples.md) ATL 範例的範例。

3. 使用 類別檢視，將方法和屬性新增至事件介面。 以滑鼠右鍵按一下 類別檢視中的類別，指向**新增**捷徑功能表，然後按一下 **加入連接點**。

4. 在 [**來源介面**清單方塊實作連接點精靈]，選取**專案的介面**。 如果您選擇的介面，為您的控制項，然後按**確定**，您將會：

   - 產生事件 proxy 類別實作的程式碼，將會發出連出呼叫事件的標頭檔案。

   - 連接點對應中新增項目。

   您也會看到您的電腦上的所有型別程式庫的清單。 您只應該使用其中一個其他型別程式庫來定義您的連接點，如果您想要實作另一個型別程式庫中找到的完全相同輸出介面。

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>若要重複使用的連接點介面，顯示在另一個型別程式庫中定義。

1. 在 類別檢視，請以滑鼠右鍵按一下類別可實作**BEGIN_COM_MAP**巨集，指向**新增**捷徑功能表，然後按一下 **加入連接點**。

2. 在實作連接點精靈中，選取 類型程式庫中的 型別程式庫和介面，然後按一下**新增**。

3. 編輯.idl 檔案為：

   - Dispinterface 複製正在使用其事件來源物件的.idl 檔中。

   - 使用**importlib**該型別程式庫的指示。

## <a name="see-also"></a>另請參閱

[連接點](../atl/atl-connection-points.md)
