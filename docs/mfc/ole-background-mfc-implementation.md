---
title: OLE 背景：MFC 實作
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 1dffdafbd02697db5aec341fec253c84217a0faf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619867"
---
# <a name="ole-background-mfc-implementation"></a>OLE 背景：MFC 實作

由於原始 OLE API 的大小和複雜度的關係，直接呼叫它來寫入 OLE 應用程式可能會非常耗時。 OLE 的 MFC 程式庫實作的目標是要減少寫入功能完整、具 OLE 功能之應用程式的工作量。

本文說明未在 MFC 內部實作的 OLE API 部分。 討論的內容也會說明如何將其對應至 Windows SDK 的 OLE 區段。

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>不是由類別庫執行的 OLE 部分

MFC 不會直接提供一些 OLE 介面和功能。 如果您要使用這些功能，您可以直接呼叫 OLE API。

IMoniker 介面 `IMoniker` ：此介面是由類別庫（例如類別）所實， `COleServerItem` 但先前並未公開給程式設計人員。 如需此介面的詳細資訊，請參閱 Windows SDK 之 OLE 區段中的 OLE 標記執行。 不過，另請參閱類別[CMonikerFile](reference/cmonikerfile-class.md)和[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)。

IUnknown 和 IMarshal 介面 `IUnknown` ：介面是由類別庫所實，但不會公開給程式設計人員。 `IMarshal`介面不是由類別庫所執行，而是在內部使用。 使用類別庫所建置的 Automation 伺服器，已經內建封送處理功能。

類別庫部分支援 Docfiles （複合檔案）複合檔案。 直接操作建立範圍外之複合檔案的函式都不受支援。 MFC 會使用類別 `COleFileStream` 來支援使用標準檔案函式的資料流程操作。 如需詳細資訊，請參閱[容器：複合檔案](containers-compound-files.md)一文。

同進程伺服器和物件處理常式同進程伺服器和物件處理常式，允許在動態連結程式庫（DLL）中執行視覺編輯資料或完整元件物件模型（COM）物件。 若要這樣做，您可以直接呼叫 OLE API 實作您的 DLL。 然而，如果您正在撰寫 Automation 伺服程式，且您的伺服程式沒有使用者介面，您可以使用 AppWizard 將您的伺服器製作成同處理序伺服器，並將其完整地置入 DLL。 如需有關這些主題的詳細資訊，請參閱[Automation 伺服器](automation-servers.md)。

> [!TIP]
> 實作 Automation 伺服程式的最簡單方法是將它放置在 DLL 中。 MFC 支援這個方法。

如需有關 Microsoft Foundation OLE 類別如何執行 OLE 介面的詳細資訊，請參閱 MFC 技術附注[38](tn038-mfc-ole-iunknown-implementation.md)、 [39](tn039-mfc-ole-automation-implementation.md)和[40](tn040-mfc-ole-in-place-resizing-and-zooming.md)。

## <a name="see-also"></a>另請參閱

[OLE 背景](ole-background.md)<br/>
[OLE 背景：實作策略](ole-background-implementation-strategies.md)
