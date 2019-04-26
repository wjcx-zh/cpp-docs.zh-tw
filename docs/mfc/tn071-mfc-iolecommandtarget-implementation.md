---
title: TN071:IOleCommandTarget 實作
ms.date: 06/28/2018
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: dca1183a17fe8f3022f517d1ad0c3932ea272417
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167994"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071:IOleCommandTarget 實作

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

`IOleCommandTarget`介面可讓物件和其容器來分派命令給彼此。 比方說，物件的工具列可能會包含命令的按鈕這類`Print`， `Print Preview`， `Save`， `New`，和`Zoom`。 如果這類物件已內嵌在支援的容器`IOleCommandTarget`，可以啟用其按鈕物件，並將其轉送至容器以進行處理，當使用者按一下這些命令。 如果容器會想要列印本身的內嵌的物件，它可能提出這項要求所傳送的命令，透過`IOleCommandTarget`內嵌物件的介面。

`IOleCommandTarget` 是自動化類似的介面，因為它正由用戶端來叫用伺服器上的方法。 不過，使用`IOleCommandTarget`儲存透過 Automation 介面進行呼叫，因為程式設計師不必使用通常很昂貴的額外負荷`Invoke`方法`IDispatch`。

在 MFC 中，`IOleCommandTarget`介面由作用中的文件伺服程式來允許將命令分派給伺服器的作用中的文件容器。 主動式文件的伺服器類別， `CDocObjectServerItem`，會使用 MFC 介面對應 (請參閱[TN038:MFC/OLE IUnknown 實作](../mfc/tn038-mfc-ole-iunknown-implementation.md)) 來實作`IOleCommandTarget`介面。

`IOleCommandTarget` 也實作於`COleFrameHook`類別。 `COleFrameHook` 是未記載的 MFC 類別，實作就地編輯容器的框架視窗功能。 `COleFrameHook` 也使用 MFC 介面對應實作`IOleCommandTarget`介面。 `COleFrameHook`實作`IOleCommandTarget`轉送 OLE 命令`COleDocObjectItem`-衍生主動式文件容器。 這可讓任何 MFC 作用中的文件容器，以接收來自包含作用中的文件伺服程式的訊息。

## <a name="mfc-ole-command-maps"></a>MFC OLE 命令對應

MFC 開發人員可以利用`IOleCommandTarget`使用 MFC OLE 命令對應。 OLE 命令對應就像訊息對應，因為它們可以用來將 OLE 命令對應到包含命令對應之類別的成員函式。 若要這麼做，請將巨集放在命令對應，以指定您想要處理的命令、 OLE 命令和命令識別碼的 OLE 命令群組[WM_COMMAND](/windows/desktop/menurc/wm-command)收到 OLE 命令時，將會傳送的訊息。 MFC 也提供幾個預先定義巨集的標準 OLE 命令。 取得一份標準的 OLE 命令原本是設計為會使用與 Microsoft Office 應用程式，，請參閱 OLECMDID 列舉型別，其定義於 docobj.h。

當包含 OLE 命令對應的 MFC 應用程式收到 OLE 命令時，MFC 會嘗試尋找所要求的命令，在 OLE 命令對應的應用程式中的命令識別碼和命令群組。 如果找到相符項目，則會將 WM_COMMAND 訊息分派至包含所要求的命令識別碼的命令對應的應用程式。 (請參閱描述`ON_OLECMD`下方。)如此一來，OLE 分派至應用程式的命令會轉變成 WM_COMMAND 訊息由 MFC。 透過使用 MFC 的標準應用程式的訊息對應會接著路由傳送 WM_COMMAND 訊息[命令路由](../mfc/command-routing.md)架構。

不同於訊息對應，MFC OLE 命令對應不會受到 ClassWizard。 MFC 開發人員必須將 OLE 命令對應支援和 OLE 命令對應項目以手動方式。 OLE 命令 WM_COMMAND 訊息路由鏈結中當時作用中的文件的是任何類別中作用中的 MFC 文件伺服程式可以加入對應是就地啟用作用中的容器中。 這些類別包括應用程式的類別衍生自[CWinApp](../mfc/reference/cwinapp-class.md)， [CView](../mfc/reference/cview-class.md)， [CDocument](../mfc/reference/cdocument-class.md)，以及[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)。 在使用中文件容器中，OLE 命令對應只會新增至[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-衍生的類別。 此外，在使用中文件容器中，WM_COMMAND 訊息只會發送至訊息對應中`COleDocObjectItem`-衍生的類別。

## <a name="ole-command-map-macros"></a>OLE 命令對應巨集

您可以使用下列巨集來將命令對應功能新增至您的類別：

```cpp
DECLARE_OLECMD_MAP ()
```

這個巨集，會包含命令對應的類別 （通常是在標頭檔） 的類別宣告中。

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
包含命令對應的類別名稱。

*baseClass*<br/>
包含命令對應之類別的基底類別的名稱。

這個巨集標記命令對應的開頭。 包含命令對應之類別的實作檔中使用這個巨集。

```
END_OLECMD_MAP()
```

這個巨集標記命令 map 的結尾。 包含命令對應之類別的實作檔中使用這個巨集。 這個巨集都必須依照 BEGIN_OLECMD_MAP 巨集。

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
OLE 命令的命令群組 GUID 的指標。 這個參數是**NULL**標準 OLE 命令群組。

*olecmdid*<br/>
要叫用命令 OLE 命令識別碼。

*id*<br/>
WM_COMMAND 訊息傳送到叫用這個 OLE 命令時，包含命令對應的應用程式的識別碼。

使用命令對應中的 ON_OLECMD 巨集，來新增您想要處理的 OLE 命令的項目。 OLE 命令收到時，它們會轉換成指定的 WM_COMMAND 訊息並透過使用標準的 MFC 命令路由架構的應用程式的訊息對應路由傳送。

## <a name="example"></a>範例

下列範例示範如何將 OLE 命令處理功能新增至使用 MFC 的文件伺服器來處理[OLECMDID_PRINT](/windows/desktop/api/docobj/ne-docobj-olecmdid) OLE 命令。 這個範例假設您使用 AppWizard 產生是使用中文件伺服器的 MFC 應用程式。

1. 在您`CView`-衍生類別的標頭檔案中，新增至類別宣告的 DECLARE_OLECMD_MAP 巨集。

    > [!NOTE]
    > 使用`CView`-衍生類別，因為它是其中一個 WM_COMMAND 訊息路由鏈結中的使用中文件伺服器中的類別。

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

2. 實作檔中`CView`-衍生的類別，新增 BEGIN_OLECMD_MAP 和 END_OLECMD_MAP 巨集：

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. 若要處理的標準 OLE 的列印命令，新增[ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd)巨集來指定標準列印命令的 OLE 命令 ID 的命令對應並**ID_FILE_PRINT** WM_COMMAND id。 **ID_FILE_PRINT**是 AppWizard 所產生的 MFC 應用程式所使用的列印命令 ID 的標準：

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

請注意，其中一個標準 OLE 命令定義的巨集，在 afxdocob.h，無法使用，來 ON_OLECMD 巨集取代因為**OLECMDID_PRINT**是標準的 OLE 命令識別碼。 ON_OLECMD_PRINT 巨集將會完成相同的工作當做 ON_OLECMD 巨集使用如上所示。

當容器應用程式傳送此伺服器**OLECMDID_PRINT**命令的伺服器透過`IOleCommandTarget`介面，MFC 列印命令處理常式將會叫用在伺服器中，導致伺服器列印應用程式。 主動式文件容器的程式碼叫用上述步驟中新增的列印命令看起來像這樣：

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
