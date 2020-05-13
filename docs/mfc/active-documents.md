---
title: 主動式文件
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: cbea3e032932477006820c5a71fbbf3e40123bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322077"
---
# <a name="active-documents"></a>主動式文件

主動式文件擴充了 OLE 的複合文件技術。 這些擴充功能是做為管理檢視的額外介面提供，如此物件就可以在容器內運作，同時保持對其顯示和列印功能的控制能力。 這個處理序能夠同時以外部框架 (例如 Microsoft Office Binder 或 Microsoft Internet Explorer) 和原生框架 (例如產品本身的檢視區) 顯示文件。

目前需要的[文件的功能要求](#requirements_for_active_documents)。 主動式文件擁有一組資料，並且可存取可儲存和擷取資料的儲存區。 它可以建立和管理其資料的一個或多個檢視。 除了支援一般 OLE 文件的內嵌和就地啟用介面之外，主動式文件還能透過 `IOleDocument` 傳達其建立檢視的能力。 透過這個介面，容器就可以建立 (可能也可以列舉) 主動式文件可顯示的檢視。 透過這個介面，主動式文件還可以提供有關本身的其他資訊，例如是否支援多個檢視或複雜的矩形。

以下是`IOleDocument`介面。 請注意,`IEnumOleDocumentViews`介面`IOleDocumentView*`是 類型的標準 OLE 枚舉器。

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

每個主動式文件都必須有使用這個介面的檢視框架提供者。 如果文件未內嵌在容器中，則主動式文件伺服程式本身必須提供檢視框架。 不過，當主動式文件內嵌在主動式文件容器中時，容器就會提供檢視框架。

活動文件可以創建其資料的一種或多種[檢視](#requirements_for_view_objects)類型(例如,普通視圖、大綱、頁面佈局等)。 檢視就像篩選，用於篩選可查看的資料。 即使文件只有一種類型的檢視,您可能仍希望支援多個檢視,作為支援新視窗功能的方法(例如,Office 應用程式中 **"視窗"** 選單上**的"新建視窗**"項)。

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>活動文件的要求

可在主動式文件容器中顯示的主動式文件必須：

- 藉由實作 `IPersistStorage`，使用 OLE 的複合檔案做為儲存機制。

- 支援 OLE 文件的基本嵌入功能,包括**從檔案建立**。 這樣就需要介面 `IPersistFile`、`IOleObject` 和 `IDataObject`。

- 支援一個或多個檢視，且每個檢視都能夠就地啟用。 也就是說,檢視`IOleDocumentView``IOleInPlaceObject`必須支援介面以及介面 和`IOleInPlaceActiveObject`(使用容器`IOleInPlaceSite``IOleInPlaceFrame`和介面)。

- 支援標準的主動式文件介面 `IOleDocument`、`IOleCommandTarget` 和 `IPrint`。

這些需求中已隱含對使用容器端介面之時機和方式的知識。

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>檢視物件的要求

主動式文件可以建立一個或多個資料檢視。 功能上來說，這些檢視就像是顯示資料之特殊方法的連接埠。 如果主動式文件只支援單一檢視，則可以使用單一類別實作主動式文件及該單一檢視。 `IOleDocument::CreateView`返回同一對象`IOleDocumentView`的 介面指標。

在活動文件容器中顯示,檢視元件必須支援`IOleInPlaceObject`除`IOleInPlaceActiveObject` `IOleDocumentView` :

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

每個檢視都有相關聯的檢視位置，其中封裝了檢視框架和檢視區 (該視窗中的 HWND 和矩形區域)。 該網站通過標準`IOleInPlaceSite`介面公開此功能。 請注意，單一 HWND 上可以有多個檢視區。

通常每一種類型的檢視都有不同的列印表示方式。 因此，檢視和對應的檢視位置應分別實作列印介面 `IPrint` 和 `IContinueCallback`。 視圖幀必須在列印開始時與視圖提供程式`IPrint`協商,以便正確列印頁眉、頁腳、邊距和相關元素。 檢視提供者會透過 `IContinueCallback` 通知框架有關列印的事件。 有關使用這些介面的詳細資訊,請參閱[程式設計列印](../mfc/programmatic-printing.md)。

請注意，如果主動式文件只支援單一檢視，則可以使用單一具象類別實作主動式文件和該單一檢視。 `IOleDocument::CreateView`只需返回同一對象`IOleDocumentView`的 介面指標。 簡單來說，如果只需要一個檢視，就不需要有兩個不同的物件執行個體。

檢視物件也可以是命令目標。 以執行`IOleCommandTarget`檢視可以接收源自容器使用者介面的指令(如 **'新增'、'****開啟**'、'**另存為'、** 在 **'檔案**'選單上**列印**;在 **"編輯"** 選單上**複製**, 貼上、**請原**復**原**) 有關詳細資訊,請參閱[訊息處理和指令目標](../mfc/message-handling-and-command-targets.md)。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](../mfc/active-document-containment.md)
