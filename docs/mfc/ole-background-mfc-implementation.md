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
ms.openlocfilehash: 25c98c3683a8656bb5188f22d0464d25a4901f49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364537"
---
# <a name="ole-background-mfc-implementation"></a>OLE 背景：MFC 實作

由於原始 OLE API 的大小和複雜度的關係，直接呼叫它來寫入 OLE 應用程式可能會非常耗時。 OLE 的 MFC 程式庫實作的目標是要減少寫入功能完整、具 OLE 功能之應用程式的工作量。

本文說明未在 MFC 內部實作的 OLE API 部分。 討論還解釋了實現的內容如何映射到 Windows SDK 的 OLE 部分。

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>類別庫未實作的 OLE 部份

MFC 不會直接提供一些 OLE 介面和功能。 如果您要使用這些功能，您可以直接呼叫 OLE API。

IMoniker`IMoniker`介面 介面由類庫(例如類)`COleServerItem`實現, 但以前未向程式師公開。 有關此介面的詳細資訊,請參閱 Windows SDK OLE 部分中的 OLE Moniker 實現。 但是,請參閱類[CMonikerFile](../mfc/reference/cmonikerfile-class.md)和[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)。

I未知介面和 IMarshal`IUnknown`介面 介面由類庫實現,但不向程式師公開。 介面`IMarshal`不是由類庫實現的,而是內部使用的。 使用類別庫所建置的 Automation 伺服器，已經內建封送處理功能。

類別庫部分支援文件檔(複合檔案)複合檔案。 直接操作建立範圍外之複合檔案的函式都不受支援。 MFC`COleFileStream`使用 類支援使用標準檔函數的流進行操作。 關於詳細資訊,請參考文章[容器:複合檔案](../mfc/containers-compound-files.md)。

進程內伺服器和物件處理程式 進程中的伺服器和物件處理程式允許在動態連結庫(DLL) 中實現可視化編輯資料或完整的元件物件模型 (COM) 物件。 若要這樣做，您可以直接呼叫 OLE API 實作您的 DLL。 然而，如果您正在撰寫 Automation 伺服程式，且您的伺服程式沒有使用者介面，您可以使用 AppWizard 將您的伺服器製作成同處理序伺服器，並將其完整地置入 DLL。 有關這些主題的詳細資訊,請參閱[自動化伺服器](../mfc/automation-servers.md)。

> [!TIP]
> 實作 Automation 伺服程式的最簡單方法是將它放置在 DLL 中。 MFC 支援這個方法。

有關 Microsoft 基礎 OLE 類別如何實現 OLE 介面的詳細資訊,請參閱 MFC 技術說明[39](../mfc/tn039-mfc-ole-automation-implementation.md)[38、39](../mfc/tn038-mfc-ole-iunknown-implementation.md)和[40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。

## <a name="see-also"></a>另請參閱

[OLE 背景](../mfc/ole-background.md)<br/>
[OLE 背景：實作策略](../mfc/ole-background-implementation-strategies.md)
