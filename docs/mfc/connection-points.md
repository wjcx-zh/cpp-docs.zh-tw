---
title: 連接點
ms.date: 11/19/2018
f1_keywords:
- IConnectionPoint
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
ms.openlocfilehash: c14d8247be2abdf828b88e728bd930691ec6571f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214148"
---
# <a name="connection-points"></a>連接點

本文說明如何使用 MFC 類別和來執行連接點（先前稱為 OLE 連接點） `CCmdTarget` `CConnectionPoint` 。

在過去，元件物件模型（COM）定義了一個一般機制（ `IUnknown::QueryInterface` *），允許物件在介面中執行並公開功能。 不過，不會定義允許物件公開其呼叫特定介面之功能的對應機制。 也就是 COM 定義了物件的連入指標（指向該物件介面的指標）的處理方式，但是沒有連出介面的明確模型（物件會保留給其他物件介面的指標）。 COM 現在具有支援這種功能的模型，稱為「連接點」。

連接有兩個部分：呼叫介面的物件，稱為來源，以及用來執行介面的物件（稱為接收）。 連接點是由來源公開的介面。 藉由公開連接點，來源可讓接收與本身建立連接（來源）。 透過連接點機制（ `IConnectionPoint` 介面），接收介面的指標會傳遞至來源物件。 這個指標會提供來源，讓您能夠存取一組成員函式的接收。 例如，若要引發接收器所執行的事件，來源可以呼叫接收器的適當方法來執行。 下圖說明剛才所述的連接點。

![已執行的連接點](../mfc/media/vc37lh1.gif "實作的連接點") <br/>
已執行的連接點

MFC 會在[CConnectionPoint](reference/cconnectionpoint-class.md)和[CCmdTarget](reference/ccmdtarget-class.md)類別中執行此模型。 衍生自的類別會 `CConnectionPoint` 執行 `IConnectionPoint` 介面，用來向其他物件公開連接點。 衍生自的類別 `CCmdTarget` 會實作為 `IConnectionPointContainer` 介面，它可以列舉物件的所有可用連接點，或尋找特定的連接點。

針對在類別中實作為的每個連接點，您必須宣告可執行連接點的連接元件。 如果您執行一或多個連接點，您也必須在類別中宣告單一連接對應。 連接對應是 ActiveX 控制項支援的連接點表格。

下列範例示範簡單的連接對應和一個連接點。 第一個範例會宣告連接對應和點。第二個範例會執行對應和點。 請注意， `CMyClass` 必須是 `CCmdTarget` 衍生的類別。 在第一個範例中，程式碼會插入類別宣告中的 **`protected`** 區段底下：

[!code-cpp[NVC_MFCConnectionPoints#1](codesnippet/cpp/connection-points_1.h)]

**BEGIN_CONNECTION_PART**和**END_CONNECTION_PART**宏會宣告可執行 `XSampleConnPt` `CConnectionPoint` 這個特定連接點的內嵌類別（衍生自）。 如果您想要覆寫任何成員函式 `CConnectionPoint` 或加入自己的成員函式，請在這兩個宏之間宣告它們。 例如，在 `CONNECTION_IID` `CConnectionPoint::GetIID` 這兩個宏之間放置時，宏會覆寫成員函式。

在第二個範例中，程式碼會插入控制項的執行檔（.cpp 檔案）中。 此程式碼會執行連接對應，其中包含連接點 `SampleConnPt` ：

[!code-cpp[NVC_MFCConnectionPoints#2](codesnippet/cpp/connection-points_2.cpp)]

如果您的類別有一個以上的連接點，請在**BEGIN_CONNECTION_MAP**和**END_CONNECTION_MAP**宏之間插入額外的**CONNECTION_PART**宏。

最後，在類別的「函式」中新增對的呼叫 `EnableConnections` 。 例如：

[!code-cpp[NVC_MFCConnectionPoints#3](codesnippet/cpp/connection-points_3.cpp)]

插入此程式碼之後，您 `CCmdTarget` 的衍生類別會公開介面的連接點 `ISampleSink` 。 下圖說明此範例。

![使用 MFC 實作的連接點](../mfc/media/vc37lh2.gif "使用 MFC 實作的連接點") <br/>
使用 MFC 實作為連接點

通常，連接點支援「多播」—這是廣播到連接到相同介面之多個接收器的功能。 下列範例片段示範如何藉由逐一查看連接點上的每個接收來進行多播：

[!code-cpp[NVC_MFCConnectionPoints#4](codesnippet/cpp/connection-points_4.cpp)]

這個範例會使用的呼叫，來抓取連接點上目前的連接集 `SampleConnPt` `CConnectionPoint::GetConnections` 。 然後，它會逐一查看連接，並 `ISampleSink::SinkFunc` 在每個使用中的連接上呼叫。

## <a name="see-also"></a>另請參閱

[MFC COM](mfc-com.md)
