---
title: "TN064：ActiveX 控制項中的 Apartment Model 執行緒 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.activex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Apartment Model 執行緒"
  - "容器 [C++], 多執行緒"
  - "多執行緒容器"
  - "OLE 控制項, 容器支援"
  - "TN064"
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN064：ActiveX 控制項中的 Apartment Model 執行緒
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個技術提示說明如何啟用 ActiveX 控制項的 Apartment Model 執行緒。  請注意 Apartment Model 執行緒在 Visual C\+\+ 4.2 版 \(含\) 以後版本才支援。  
  
## 什麼是 Apartment Model 執行緒?  
 Apartment 模型是方法對支援內嵌物件，例如 ActiveX 控制項，在多執行緒的容器應用程式內。  雖然應用程式可能具有多執行緒，內嵌物件的每個執行個體將指派給單一執行緒 Apartment 「，」一執行緒才會執行。  換句話說，所有呼叫控制項的執行個體內的相同執行緒上發生。  
  
 不過，同一個控制項的不同執行個體可以指派給不同的 Apartment。  對這個的，因此，如果控制項的多個執行個體共用任何資料共同的 \(例如，靜態或全域資料\)，然後存取共用資料必須受同步物件的保護，例如關鍵區段。  
  
 如需在 Apartment 執行緒模型的完整詳細資訊，請參閱《 *OLE 程式設計人員參考》的*[處理序和執行緒](http://msdn.microsoft.com/library/windows/desktop/ms684841) 。  
  
## 為什麼支援 Apartment Model 執行緒?  
 支援 Apartment Model 執行緒的控制項也支援 Apartment 模型的多執行緒的容器應用程式。  如果不啟用 Apartment Model 執行緒，您可能會限制您的控制項可以使用的設定容器。  
  
 特別是如果它們有少許或不使用共用資料，啟用 Apartment Model 執行緒對大部分控制項都可以。  
  
## 保護共用資料  
 如果您的控制項共用資料，例如靜態成員變數，請存取該應該保護資料以關鍵區段防止多個執行緒同時修改資料。  若要針對此目的設定關鍵區段，請宣告類別 `CCriticalSection` 的靜態成員變數在您的控制項的類別。  使用這個關鍵區段物件的 `Lock` 和 **Unlock** 成員函式的地方，您的程式碼存取共用資料。  
  
 考量，例如，需要保留字串的所有執行個體共用的控制項類別。  這個字串使用靜態成員變數可以維護和受關鍵區段 \(Critical Section\) 保護。  控制項的類別宣告中包含下列項目:  
  
```  
class CSampleCtrl : public COleControl  
{  
    ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 類別的實作將包含這些變數的定義:  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 對 `_strShared` 之靜態成員的存取可能受關鍵區段則保護:  
  
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
  
## 註冊 Apartment Model 明確的控制項  
 支援 Apartment Model 執行緒的控制項應該將具名值表示註冊這個功能， 「ThreadingModel」與「Apartment」值在其類別 ID 登錄項目在 *類別 ID*\\**InprocServer32** 機碼。  若要讓這個金鑰便會自動註冊控制項，請將第六個參數的 `afxRegApartmentThreading` 旗標為 `AfxOleRegisterControlClass`:  
  
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
        return AfxOleUnregisterClass(m_clsid, m_lpszProgID);  
}  
```  
  
 如果控制項專案是以 Visual C\+\+ 4.1 版 \(含\) 以後版本的 ControlWizard 產生，這個旗標會已經是存在於您的程式碼。  變更不需要註冊執行緒模型。  
  
 如果您的專案是 ControlWizard 舊版產生，將現有的程式碼將具有布林值做為第六個參數。  如果現有的參數為 true 時，請將它加入至`afxRegInsertable | afxRegApartmentThreading`。  如果現有的參數為 false，請將它加入至`afxRegApartmentThreading`。  
  
 如果控制項不符合 Apartment Model 執行緒的規則，您不能將這個參數的 `afxRegApartmentThreading` 。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)