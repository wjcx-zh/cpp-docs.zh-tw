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
ms.openlocfilehash: e6f8161432cc951b5e224ec28142429efbdf0726
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639656"
---
# <a name="active-documents"></a>主動式文件

主動式文件擴充了 OLE 的複合文件技術。 這些擴充功能是做為管理檢視的額外介面提供，如此物件就可以在容器內運作，同時保持對其顯示和列印功能的控制能力。 這個處理序能夠同時以外部框架 (例如 Microsoft Office Binder 或 Microsoft Internet Explorer) 和原生框架 (例如產品本身的檢視區) 顯示文件。

本節說明功能性[主動式文件的需求](#requirements_for_active_documents)。 主動式文件擁有一組資料，並且可存取可儲存和擷取資料的儲存區。 它可以建立和管理其資料的一個或多個檢視。 除了支援一般 OLE 文件的內嵌和就地啟用介面之外，主動式文件還能透過 `IOleDocument` 傳達其建立檢視的能力。 透過這個介面，容器就可以建立 (可能也可以列舉) 主動式文件可顯示的檢視。 透過這個介面，主動式文件還可以提供有關本身的其他資訊，例如是否支援多個檢視或複雜的矩形。

以下是`IOleDocument`介面。 請注意，`IEnumOleDocumentViews`介面是標準 OLE 列舉值`IOleDocumentView*`型別。

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

主動式文件可以建立一或多個類型[檢視](#requirements_for_view_objects)它的資料 （例如，標準，大綱、 頁面配置，等等）。 檢視就像篩選，用於篩選可查看的資料。 即使文件有一種檢視，您仍可能想要做為支援新的視窗功能的支援多個檢視 (例如**開新視窗**項目上**視窗**Office 中的功能表應用程式）。

##  <a name="requirements_for_active_documents"></a> 主動式文件的需求

可在主動式文件容器中顯示的主動式文件必須：

- 藉由實作 `IPersistStorage`，使用 OLE 的複合檔案做為儲存機制。

- 支援 OLE 文件，包括基本的內嵌功能**從檔案建立**。 這樣就需要介面 `IPersistFile`、`IOleObject` 和 `IDataObject`。

- 支援一個或多個檢視，且每個檢視都能夠就地啟用。 亦即，檢視必須支援介面`IOleDocumentView`介面以及`IOleInPlaceObject`並`IOleInPlaceActiveObject`(使用容器`IOleInPlaceSite`和`IOleInPlaceFrame`介面)。

- 支援標準的主動式文件介面 `IOleDocument`、`IOleCommandTarget` 和 `IPrint`。

這些需求中已隱含對使用容器端介面之時機和方式的知識。

##  <a name="requirements_for_view_objects"></a> 檢視物件的需求

主動式文件可以建立一個或多個資料檢視。 功能上來說，這些檢視就像是顯示資料之特殊方法的連接埠。 如果主動式文件只支援單一檢視，則可以使用單一類別實作主動式文件及該單一檢視。 `IOleDocument::CreateView` 會傳回相同物件的`IOleDocumentView`介面指標。

若要表示使用中文件容器內，檢視元件必須支援`IOleInPlaceObject`並`IOleInPlaceActiveObject`除了`IOleDocumentView`:

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

每個檢視都有相關聯的檢視位置，其中封裝了檢視框架和檢視區 (該視窗中的 HWND 和矩形區域)。 公開這項功能雖然標準`IOleInPlaceSite`介面。 請注意，單一 HWND 上可以有多個檢視區。

通常每一種類型的檢視都有不同的列印表示方式。 因此，檢視和對應的檢視位置應分別實作列印介面 `IPrint` 和 `IContinueCallback`。 檢視框架必須與檢視提供者透過交涉`IPrint`列印開始時，如此才能正確列印頁首、 頁尾、 邊界和相關項目。 檢視提供者會透過 `IContinueCallback` 通知框架有關列印的事件。 如需使用這些介面的詳細資訊，請參閱 <<c0> [ 以程式設計方式列印](../mfc/programmatic-printing.md)。

請注意，如果主動式文件只支援單一檢視，則可以使用單一具象類別實作主動式文件和該單一檢視。 `IOleDocument::CreateView` 只會傳回相同的物件`IOleDocumentView`介面指標。 簡單來說，如果只需要一個檢視，就不需要有兩個不同的物件執行個體。

檢視物件也可以是命令目標。 藉由實作`IOleCommandTarget`檢視可以接收來自容器的使用者介面中的命令 (例如**新增**， **Open**，**另存新檔**， **列印**上**檔案**功能表，並**複製**，**貼上**，**復原**上**編輯**  功能表)。 如需詳細資訊，請參閱 <<c0> [ 訊息處理和命令目標](../mfc/message-handling-and-command-targets.md)。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](../mfc/active-document-containment.md)

