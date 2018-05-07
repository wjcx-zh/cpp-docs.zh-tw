---
title: 'TN064: ActiveX 控制項中的 Apartment Model 執行緒 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 515103fc66ad221a3806fc101dcbc01f507ef535
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064：ActiveX 控制項中的 Apartment Model 執行緒
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個技術提示說明如何啟用 ActiveX 控制項中的 apartment model 執行緒。 請注意，apartment model 執行緒是只在 4.2 或更新版本的 Visual c + + 版本中。  
  
## <a name="what-is-apartment-model-threading"></a>Apartment Model 執行緒是什麼  
 Apartment 模型是一種方法支援內嵌的物件，例如 ActiveX 控制項，在多執行緒的容器應用程式中。 雖然應用程式可能有多個執行緒，每個執行個體的內嵌物件會指派為一個 「 apartment，「 只有一個執行緒上執行。 換句話說，所有對控制項的執行個體的呼叫將會發生在相同執行緒上。  
  
 不過，相同的控制項類型的不同執行個體可能會指派給不同的 apartment。 因此，如果控制項的多個執行個體共用通用 （例如，靜態或全域資料） 中的任何資料，存取此共用的資料將需要受同步處理物件，例如關鍵區段。  
  
 如需 apartment 執行緒模式的完整詳細資訊，請參閱[處理序和執行緒](http://msdn.microsoft.com/library/windows/desktop/ms684841)中*OLE 程式設計人員參考*。  
  
## <a name="why-support-apartment-model-threading"></a>為什麼支援 Apartment Model 執行緒  
 也支援 apartment 模型的多執行緒的容器應用程式中，就可以使用支援 apartment model 執行緒的控制項。 如果您未啟用 apartment model 執行緒，您將會限制可能無法在其中使用您的控制項的容器一組。  
  
 啟用 apartment model 執行緒很容易大部分的控制項，特別是當他們有少量或沒有共用的資料。  
  
## <a name="protecting-shared-data"></a>保護共用資料  
 如果您的控制項使用共用的資料，例如靜態成員變數，存取資料應受到保護以防止多個執行緒同時修改資料的重要區段。 若要設定針對此用途的重要區段，宣告類別的靜態成員變數`CCriticalSection`控制項的類別中。 使用`Lock`和**Unlock**這個關鍵區段的成員函式物件，只要您的程式碼存取的共用的資料。  
  
 例如，考慮需要維護共用的所有執行個體的字串控制項類別。 這個字串可以在靜態成員變數中維護，保護的重要區段。 控制項的類別宣告就會包含下列各項：  
  
```  
class CSampleCtrl : public COleControl  
{  
 ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 此類別的實作會包含這些變數的定義：  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 若要存取`_strShared`關鍵區段就可以保護靜態成員：  
  
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
  
## <a name="registering-an-apartment-model-aware-control"></a>註冊 Apartment 模型感知的控制項  
 支援 apartment model 執行緒的控制項應該在其類別識別碼登錄項目中的 「 Apartment 」 值加上"ThreadingModel 」 的具名的值會指出在登錄中，這項功能*類別識別碼*\\ **InprocServer32**索引鍵。 若要使這個機碼來自動註冊您的控制項，傳遞`afxRegApartmentThreading`第六個參數中的旗標`AfxOleRegisterControlClass`:  
  
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
  
 如果您的控制項專案所產生 ControlWizard Visual c + + 版本 4.1 或更新版本中，已經會出現在您的程式碼這個旗標。 不不需要註冊的執行緒模型的任何變更。  
  
 如果您的專案由舊版的 ControlWizard 產生，現有的程式碼將第六個參數有布林值。 如果現有的參數為 TRUE，將它變更為`afxRegInsertable | afxRegApartmentThreading`。 如果現有的參數為 FALSE，將它變更為`afxRegApartmentThreading`。  
  
 如果您的控制項不符合 apartment model 執行緒的規則，您必須傳遞`afxRegApartmentThreading`此參數中。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

