---
title: TN064：ActiveX 控制項中的 Apartment Model 執行緒
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 0c6a42124b4b2b03ae7cd9277fa14d43eac7a2bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366062"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064：ActiveX 控制項中的 Apartment Model 執行緒

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本技術說明說明如何在 ActiveX 控件中啟用公寓模型線程。 請注意,公寓模型線程僅在視覺C++版本 4.2 或更高版本中支援。

## <a name="what-is-apartment-model-threading"></a>什麼是公寓-模型線程

單元模型是支援多線程容器應用程式中的嵌入式物件(如 ActiveX 控制項)的方法。 儘管應用程式可能有多個線程,但嵌入物件的每個實例都將分配給一個「單元」,該「單元」將僅在一個線程上執行。 換句話說,對控件實例的所有調用都將在同一線程上發生。

但是,同一類型的控制的不同實例可能分配給不同的公寓。 因此,如果控件的多個實例共用任何通用數據(例如靜態或全域數據),則需要通過同步物件(如關鍵部分)保護對此共享數據的訪問。

有關公寓線程模型的完整詳細資訊,請參閱*OLE 程式師參考*中的[「進程和線程](/windows/win32/ProcThread/processes-and-threads)」。

## <a name="why-support-apartment-model-threading"></a>為什麼支援公寓-模型線程

支援單元模型線程的控制項可用於支援單元模型的多線程容器應用程式。 如果不啟用公寓模型線程,將限制可以使用控件的潛在容器集。

對於大多數控件來說,啟用公寓模型線程很容易,尤其是當它們幾乎沒有共享數據時。

## <a name="protecting-shared-data"></a>保護共享資料

如果控件使用共享數據(如靜態成員變數),則應使用關鍵部分保護對該數據的訪問,以防止多個線程同時修改數據。 為此設置關鍵部分,請聲明控制件類中的類`CCriticalSection`的靜態成員變數。 無論代碼`Lock`存`Unlock`取 共享資料的位置,都使用此關鍵部分物件的和成員函數。

例如,考慮需要維護由所有實例共用的字串的控制項類。 此字串可以保存在靜態成員變數中,並由關鍵部分保護。 控制項的類別聲明包含以下內容:

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

類別的設定為這些變數的定義:

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

然後,可以`_strShared`通過 關鍵部分保護對靜態成員的訪問:

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>註冊公寓模型感知控制

支援公寓模型線程的控制項應在註冊表中指示此功能,在*類ID*\\**InprocServer32**鍵下的類ID 註冊表條目中添加具有"公寓"值的命名值"線程模型"。 要讓此金鑰自動註冊以進行控制,請將第六個參數中的*afxReg 公寓線程*`AfxOleRegisterControlClass`標誌傳遞給 :

```cpp
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

如果控件專案由 VisualC++ 版 4.1 或更高版本的 ControlWizard 生成,則此標誌將已經在代碼中存在。 註冊線程模型不需要任何更改。

如果專案由早期版本的 ControlWizard 生成,則現有代碼將具有布林值作為第六個參數。 如果現有參數為 TRUE,請將它更改為*afxReg 可插入 = afxReg公寓線程*。 如果現有參數為 FALSE,則將其更改為*afxReg 公寓線程*。

如果您的控制項未遵循公寓模型線程的規則,則不得在此參數中傳遞*afxReg公寓線程*。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
