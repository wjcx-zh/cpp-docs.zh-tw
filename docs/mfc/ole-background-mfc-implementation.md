---
title: OLE 背景： MFC 實作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IMarshall
- IMoniker
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d6fdd0fa05ec21151a28c516adcb224f5e9b0ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409827"
---
# <a name="ole-background-mfc-implementation"></a>OLE 背景：MFC 實作

由於原始 OLE API 的大小和複雜度的關係，直接呼叫它來寫入 OLE 應用程式可能會非常耗時。 OLE 的 MFC 程式庫實作的目標是要減少寫入功能完整、具 OLE 功能之應用程式的工作量。

本文說明未在 MFC 內部實作的 OLE API 部分。 討論內容也會說明如何實作對應的 OLE 部分的 Windows SDK。

##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> 類別庫未實作的 OLE 的部分

MFC 不會直接提供一些 OLE 介面和功能。 如果您要使用這些功能，您可以直接呼叫 OLE API。

IMoniker 介面`IMoniker`介面由類別庫實作 (例如`COleServerItem`類別)，但有先前未公開給程式設計人員。 如需有關此介面的詳細資訊，請參閱 OLE Moniker 實作的 OLE 部分的 Windows SDK。 不過，請參閱類別[CMonikerFile](../mfc/reference/cmonikerfile-class.md)並[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)。

IUnknown 和 IMarshal 介面`IUnknown`介面由類別庫所實作，但不是會公開給程式設計人員。 `IMarshal`介面不會實作類別庫，但會在內部使用。 使用類別庫所建置的 Automation 伺服器，已經內建封送處理功能。

Docfiles （複合檔案） 複合檔案部分類別程式庫所支援。 直接操作建立範圍外之複合檔案的函式都不受支援。 MFC 會使用類別`COleFileStream`來支援標準檔案函式的資料流的操作。 如需詳細資訊，請參閱文章[容器： 複合檔案](../mfc/containers-compound-files.md)。

同處理序伺服器和物件處理常式中的處理序伺服器和物件處理常式可讓實作視覺編輯資料或動態連結程式庫 (DLL) 中的完整元件物件模型 (COM) 物件。 若要這樣做，您可以直接呼叫 OLE API 實作您的 DLL。 然而，如果您正在撰寫 Automation 伺服程式，且您的伺服程式沒有使用者介面，您可以使用 AppWizard 將您的伺服器製作成同處理序伺服器，並將其完整地置入 DLL。 如需有關這些主題的詳細資訊，請參閱 < [Automation 伺服程式](../mfc/automation-servers.md)。

> [!TIP]
>  實作 Automation 伺服程式的最簡單方法是將它放置在 DLL 中。 MFC 支援這個方法。

如需有關 Microsoft Foundation OLE 類別如何實作 OLE 介面的詳細資訊，請參閱 MFC 技術提示[38](../mfc/tn038-mfc-ole-iunknown-implementation.md)， [39](../mfc/tn039-mfc-ole-automation-implementation.md)，並[40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。

## <a name="see-also"></a>另請參閱

[OLE 背景](../mfc/ole-background.md)<br/>
[OLE 背景：實作策略](../mfc/ole-background-implementation-strategies.md)

