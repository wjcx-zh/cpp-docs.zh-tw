---
title: 網際網路上的非同步 Moniker
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: 74add1ad894f883c67eefab888898c0abf518b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625039"
---
# <a name="asynchronous-monikers-on-the-internet"></a>網際網路上的非同步 Moniker

由於網路存取的速度很慢，網際網路需要加入新的方法至應用程式設計。 應用程式應該以非同步方式執行網路存取，避免讓使用者介面失去作用。 MFC 類別[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)提供下載檔案的非同步支援。

有了非同步 Moniker，您可以擴充 COM 應用程式，使其跨網際網路進行非同步下載，並提供大型物件的漸進式呈現，例如點陣圖和 VRML 物件。 非同步 Moniker 可下載網際網路上的 ActiveX 控制項屬性或檔案，而不會封鎖使用者介面的回應。

## <a name="advantages-of-asynchronous-monikers"></a>非同步 Moniker 的優點

您可以使用非同步 Moniker 進行下列動作：

- 下載程式碼和檔案而不會封鎖。

- 在 ActiveX 控制項中下載屬性，而不會封鎖。

- 接收下載進度的通知。

- 追蹤進度和就緒狀態資訊。

- 提供進度的狀態資訊給使用者。

- 允許使用者隨時取消下載。

## <a name="mfc-classes-for-asynchronous-monikers"></a>非同步 Moniker 的 MFC 類別

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)衍生自[CMonikerFile](reference/cmonikerfile-class.md)，而後者又衍生自[COleStreamFile](reference/colestreamfile-class.md)。 `COleStreamFile` 物件表示一種資料流；`CMonikerFile` 物件會使用 `IMoniker` 取得資料，而 `CAsyncMonikerFile` 也會以非同步方式如此做。

非同步 Moniker 主要在支援網際網路的應用程式和 ActiveX 控制項中使用，用於在檔案傳輸期間提供反應靈敏的使用者介面。 其主要的範例是使用[CDataPathProperty](reference/cdatapathproperty-class.md)來提供 ActiveX 控制項的非同步屬性。

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>MFC 類別在 ActiveX 控制項中的資料路徑

MFC 類別 `CDataPathProperty` 和[CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md)會執行可非同步載入的 ActiveX 控制項屬性。 非同步屬性會在同步初始之後載入。 非同步 ActiveX 控制項會重複叫用回呼，在長時間的屬性交換過程中表示新資料的可用性。

`CDataPathProperty` 衍生自 `CAsyncMonikerFile`。 `CCachedDataPathProperty` 衍生自 `CDataPathProperty`。 若要在您的 ActiveX 控制項中執行非同步屬性，請從或衍生類別， `CDataPathProperty` `CCachedDataPathProperty` 並覆寫[OnDataAvailable](reference/casyncmonikerfile-class.md#ondataavailable)和您想要接收的其他通知。

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>使用非同步 Moniker 下載檔案

1. 宣告衍生自[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)的類別。

1. 覆寫[OnDataAvailable](reference/casyncmonikerfile-class.md#ondataavailable)以顯示資料。

1. 覆寫其他成員函式，包括[OnProgress](reference/casyncmonikerfile-class.md#onprogress)、 [OnStartBinding](reference/casyncmonikerfile-class.md#onstartbinding)和[OnStopBinding](reference/casyncmonikerfile-class.md#onstopbinding)。

1. 宣告這個類別的執行個體並使用它來開啟 URL。

如需在 ActiveX 控制項中以非同步方式下載的詳細資訊，請參閱[網際網路上的 ActiveX 控制項](activex-controls-on-the-internet.md)。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](mfc-internet-programming-basics.md)
