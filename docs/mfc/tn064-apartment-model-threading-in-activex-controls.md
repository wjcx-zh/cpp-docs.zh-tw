---
title: TN064：ActiveX 控制項中的單元模型執行緒
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 2c6b9dd3ed244f7169e5055eebe7a34e3345e841
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513332"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064：ActiveX 控制項中的單元模型執行緒

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本技術提示說明如何在 ActiveX 控制項中啟用單元模型執行緒。 請注意, 只有在 Visual C++ 4.2 版或更新版本中才支援單元模型執行緒。

## <a name="what-is-apartment-model-threading"></a>什麼是單元模型執行緒

「單元模型」是一種在多執行緒容器應用程式中支援内嵌物件 (例如 ActiveX 控制項) 的方法。 雖然應用程式可能會有多個執行緒, 但每個内嵌物件的實例都會指派給一個 "公寓", 而這只會在一個執行緒上執行。 換句話說, 所有對控制項實例的呼叫都會在同一個執行緒上發生。

不過, 相同控制項類型的不同實例可能會指派給不同的單元。 因此, 如果控制項的多個實例共用任何共同的資料 (例如, 靜態或全域資料), 則必須由同步處理物件 (例如重要區段) 來保護此共用資料的存取。

如需有關單元執行緒模型的完整詳細資料, 請參閱 OLE 程式設計*人員參考*中的[進程和執行緒](/windows/win32/ProcThread/processes-and-threads)。

## <a name="why-support-apartment-model-threading"></a>為何支援單元模型執行緒

支援單元模型執行緒的控制項可用於也支援單元模型的多執行緒容器應用程式。 如果您未啟用單元模型執行緒, 您將會限制可以使用控制項的可能容器集合。

對於大部分的控制項而言, 啟用單元模型執行緒很容易, 特別是在沒有共用資料的情況下。

## <a name="protecting-shared-data"></a>保護共用資料

如果您的控制項使用共用資料 (例如靜態成員變數), 則應該使用重要區段來保護該資料的存取, 以避免一個以上的執行緒同時修改資料。 若要為此目的設定重要區段, 請在控制項的類別中宣告類別`CCriticalSection`的靜態成員變數。 只要您`Lock`的`Unlock`程式碼存取共用資料, 請使用這個重要區段物件的和成員函式。

例如, 請考慮需要維護所有實例共用之字串的控制項類別。 這個字串可以在靜態成員變數中維護, 並受到重要區段的保護。 控制項的類別宣告會包含下列內容:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

類別的執行會包含這些變數的定義:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

`_strShared`存取靜態成員之後就可以受到重要區段的保護:

```
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>註冊單元模型感知控制項

支援單元模型執行緒的控制項應該在登錄中指出這項功能, 方法是在其類別識別碼登錄專案的*類別識別碼*\\ **底下, 新增名為 "ThreadingModel" 且值為 "公寓"InprocServer32**鍵。 若要讓此金鑰自動註冊給您的控制項, 請將第六個參數中的 afxRegApartmentThreading `AfxOleRegisterControlClass`旗標傳遞給:

```
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)
{
    if (bRegister)
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(),
    m_clsid,
    m_lpszProgID,
    IDS_SAMPLE,
    IDB_SAMPLE,
    afxRegApartmentThreading,
    _dwSampleOleMisc,
    _tlid,
    _wVerMajor,
    _wVerMinor);

else
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}
```

如果您的控制項專案是由 Visual C++ 4.1 版或更新版本中的 ControlWizard 所產生, 則此旗標將會出現在您的程式碼中。 註冊執行緒模型不需要任何變更。

如果您的專案是由舊版的 ControlWizard 所產生, 您現有的程式碼將會有一個布林值做為第六個參數。 如果現有的參數為 TRUE, 請將它變更為*afxRegInsertable | afxRegApartmentThreading*。 如果現有的參數為 FALSE, 請將它變更為*afxRegApartmentThreading*。

如果您的控制項並未遵循單元模型執行緒的規則, 您就不能在這個參數中傳遞*afxRegApartmentThreading* 。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
