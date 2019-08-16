---
title: TN071：MFC IOleCommandTarget 的執行
ms.date: 06/28/2018
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 7077211396c68750d47b91c7b2bb113370990f62
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511096"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071：MFC IOleCommandTarget 的執行

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

`IOleCommandTarget`介面可讓物件和其容器分派命令給彼此。 例如, 物件的`Print`工具列可能包含命令的按鈕, 例如、 `Print Preview`、 `Save`、 `New`和`Zoom`。 如果這類物件內嵌在支援`IOleCommandTarget`的容器中, 則物件可以啟用其按鈕, 並將命令轉送至容器, 以便在使用者按一下時進行處理。 如果容器想要讓内嵌物件自行列印, 它可以透過内嵌物件的`IOleCommandTarget`介面傳送命令來提出此要求。

`IOleCommandTarget`是類似 Automation 的介面, 可讓用戶端用來叫用伺服器上的方法。 不過, 使用`IOleCommandTarget`會節省透過 Automation 介面進行呼叫的額外負荷, 因為程式設計人員不需要使用`Invoke`通常昂貴`IDispatch`的方法。

在 MFC 中, `IOleCommandTarget`活動文檔伺服器會使用此介面來允許活動文檔容器將命令分派至伺服器。 活動文檔伺服器類別`CDocObjectServerItem`使用 MFC 介面對應 (請參閱[TN038:MFC/OLE IUnknown 執行](../mfc/tn038-mfc-ole-iunknown-implementation.md)) 來`IOleCommandTarget`執行介面。

`IOleCommandTarget`也會在`COleFrameHook`類別中執行。 `COleFrameHook`是未記載的 MFC 類別, 可執行就地編輯容器的框架視窗功能。 `COleFrameHook`也會使用 MFC 介面對應來執行`IOleCommandTarget`介面。 `COleFrameHook`的執行會`IOleCommandTarget`將 OLE 命令轉送`COleDocObjectItem`至衍生的活動文檔容器。 這可讓任何 MFC 使用中檔容器從包含的現用文檔伺服器接收訊息。

## <a name="mfc-ole-command-maps"></a>MFC OLE 命令對應

Mfc 開發人員可以`IOleCommandTarget`利用 mfc OLE 命令對應來使用。 OLE 命令對應就像訊息對應, 因為它們可以用來將 OLE 命令對應至包含命令對應之類別的成員函式。 若要進行這項工作, 請將宏放在命令對應中, 以指定您想要處理之命令的 OLE 命令群組、OLE 命令, 以及收到 OLE 命令時將傳送之[WM_COMMAND](/windows/win32/menurc/wm-command)訊息的命令識別碼。 MFC 也針對標準的 OLE 命令提供了許多預先定義的宏。 如需原先設計用於 Microsoft Office 應用程式的標準 OLE 命令清單, 請參閱 OLECMDID 列舉 (定義于 docobj.idl)。

當包含 OLE 命令對應的 MFC 應用程式收到 OLE 命令時, MFC 會嘗試在應用程式的 OLE 命令對應中, 尋找所要求之命令的命令 ID 和命令群組。 如果找到相符的結果, 則會將 WM_COMMAND 訊息分派至包含命令對應的應用程式, 並提供所要求之命令的識別碼。 (請參閱`ON_OLECMD`下面的說明)。如此一來, 分派至應用程式的 OLE 命令就會由 MFC 轉換成 WM_COMMAND 訊息。 然後會使用 MFC 標準[命令路由](../mfc/command-routing.md)架構, 透過應用程式的訊息對應來路由傳送 WM_COMMAND 訊息。

與訊息對應不同的是, ClassWizard 不支援 MFC OLE 命令對應。 MFC 開發人員必須手動加入 OLE 命令對應支援和 OLE 命令對應專案。 當使用中的檔在容器中就地作用時, 可以將 OLE 命令對應加入至 WM_COMMAND 訊息路由鏈中任何類別的 MFC 活動文檔伺服器。 這些類別包括衍生自[CWinApp](../mfc/reference/cwinapp-class.md)、 [CView](../mfc/reference/cview-class.md)、 [CDocument](../mfc/reference/cdocument-class.md)和[coleipframewnd 來衍生](../mfc/reference/coleipframewnd-class.md)的應用程式類別。 在活動文檔容器中, OLE 命令對應只能加入至[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)衍生類別。 此外, 在活動文檔容器中, WM_COMMAND 訊息只會分派至衍生類別中`COleDocObjectItem`的訊息對應。

## <a name="ole-command-map-macros"></a>OLE 命令對應宏

使用下列宏將命令對應功能新增至您的類別:

```cpp
DECLARE_OLECMD_MAP ()
```

這個宏會進入包含命令對應之類別的類別宣告 (通常是在標頭檔中)。

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
包含命令對應的類別名稱。

*baseClass*<br/>
包含命令對應之類別的基類名稱。

這個宏會標示命令對應的開頭。 請在包含命令對應之類別的執行檔案中使用此宏。

```
END_OLECMD_MAP()
```

這個宏會標示命令對應的結尾。 請在包含命令對應之類別的執行檔案中使用此宏。 這個宏必須一律跟隨在 BEGIN_OLECMD_MAP 宏的後面。

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
OLE 命令的命令群組之 GUID 的指標。 標準 OLE 命令群組的此參數為**Null** 。

*olecmdid*<br/>
要叫用之命令的 OLE 命令識別碼。

*id*<br/>
叫用此 OLE 命令時, 要傳送至包含命令對應之應用程式的 WM_COMMAND 訊息識別碼。

在命令對應中使用 ON_OLECMD 宏, 為您要處理的 OLE 命令新增專案。 收到 OLE 命令時, 會將它們轉換成指定的 WM_COMMAND 訊息, 並使用標準 MFC 命令路由架構, 透過應用程式的訊息對應來路由傳送。

## <a name="example"></a>範例

下列範例顯示如何將 OLE 命令處理功能加入至 MFC 使用中文檔伺服器, 以處理[OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) OLE 命令。 這個範例假設您使用了啟動程式來產生屬於活動文檔伺服器的 MFC 應用程式。

1. `CView`在衍生類別的標頭檔中, 將 DECLARE_OLECMD_MAP 宏新增至類別宣告。

    > [!NOTE]
    > `CView`使用衍生類別, 因為它是活動文檔伺服器中的其中一個類別, 位於 WM_COMMAND 訊息路由鏈中。

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. 在衍生類別的執行`CView`檔案中, 新增 BEGIN_OLECMD_MAP 和 END_OLECMD_MAP 宏:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. 若要處理標準的 OLE 列印命令, 請在命令對應中新增[ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd)宏, 指定標準 print 命令的 OLE 命令識別碼, 並針對 WM_COMMAND 識別碼指定**ID_FILE_PRINT** 。 **ID_FILE_PRINT**是由程式層產生的 MFC 應用程式所使用的標準列印命令識別碼:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

請注意, 您可以使用 afxdocob 中定義的其中一個標準 OLE 命令宏來取代 ON_OLECMD 宏, 因為**OLECMDID_PRINT**是標準的 OLE 命令識別碼。 ON_OLECMD_PRINT 宏會完成與上面所示的 ON_OLECMD 宏相同的工作。

當容器應用程式透過伺服器的`IOleCommandTarget`介面傳送**OLECMDID_PRINT**命令給此伺服器時, 將會在伺服器中叫用 MFC 列印命令處理常式, 使伺服器列印應用程式。 活動文檔容器的程式碼若要叫用上述步驟中新增的列印命令, 如下所示:

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
