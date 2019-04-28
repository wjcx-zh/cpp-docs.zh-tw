---
title: TN064:Apartment Model 執行緒在 ActiveX 控制項
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
ms.openlocfilehash: d6f02b2106693226f6380e935a54e04e10d5b4f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351822"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064:Apartment Model 執行緒在 ActiveX 控制項

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

這個技術提示說明如何啟用 ActiveX 控制項中的 apartment model 執行緒。 請注意，apartment model 執行緒只支援在視覺效果C++4.2 或更新版本的版本。

## <a name="what-is-apartment-model-threading"></a>什麼是 Apartment Model 執行緒

公寓模型是一種方法支援內嵌的物件，例如 ActiveX 控制項，在多執行緒的容器應用程式中。 雖然應用程式可能有多個執行緒，每個內嵌物件執行個體將會指派至 「 apartment，「 只有一個執行緒上執行。 也就是說，控制項的執行個體的所有呼叫將會都發生在相同的執行緒。

不過，相同的控制項類型的不同執行個體可能會指派給不同的 apartment。 因此，如果控制項的多個執行個體共用常見 （例如，靜態或全域資料） 中的任何資料，再存取此共用的資料必須受到同步處理物件，例如關鍵區段。

如需 apartment 執行緒模型的完整詳細資訊，請參閱[處理序和執行緒](/windows/desktop/ProcThread/processes-and-threads)中*OLE 程式設計人員參考*。

## <a name="why-support-apartment-model-threading"></a>為什麼要支援的 Apartment Model 執行緒

控制項支援的 apartment model 執行緒可用也支援 apartment 模型的多執行緒的容器應用程式中使用。 如果您未啟用的 apartment model 執行緒，您將會限制潛在的容器可以在其中使用您的控制項集合。

啟用的 apartment model 執行緒很容易對於大部分的控制項，特別是當它們有少量或沒有共用的資料。

## <a name="protecting-shared-data"></a>保護共用的資料

如果您的控制項使用的共用的資料，例如靜態成員變數，存取資料應受到保護以防止多個執行緒同時修改資料的重要區段。 若要設定針對此目的的重要區段，宣告類別的靜態成員變數`CCriticalSection`控制項的類別中。 使用`Lock`和`Unlock`這個關鍵區段之成員函式物件，只要您的程式碼存取的共用的資料。

例如，考慮需要維護共用的所有執行個體的字串控制項類別。 此字串可以在靜態成員變數中維護，並保護重要的區段。 控制項的類別宣告會包含下列內容：

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

類別的實作會包含這些變數的定義：

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

若要存取`_strShared`靜態成員接著就可以受重要區段：

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

## <a name="registering-an-apartment-model-aware-control"></a>註冊的 Apartment 感知模型感知控制項

支援的 apartment model 執行緒的控制項應該在其類別識別碼登錄項目中的 「 Apartment 」 值加上"ThreadingModel 」 的具名的值會指出在登錄中，這項功能*類別識別碼*\\ **InprocServer32**索引鍵。 若要讓此金鑰會自動為您的控制項註冊，請傳遞*afxRegApartmentThreading*中的第六個參數的旗標`AfxOleRegisterControlClass`:

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

如果您的控制項專案由 ControlWizard 視覺效果中產生C++4.1 或更新版本的版本，這個旗標將會出現在程式碼中。 不不需要註冊的執行緒模型的任何變更。

如果您的專案由舊版 ControlWizard 產生，您現有的程式碼會有布林值，做為第六個參數。 如果現有的參數為 TRUE，將它變更為*afxRegInsertable | afxRegApartmentThreading*。 如果現有的參數為 FALSE，將它變更為*afxRegApartmentThreading*。

如果您的控制項不會遵循 apartment model 執行緒規則，您必須傳遞*afxRegApartmentThreading*此參數中。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
