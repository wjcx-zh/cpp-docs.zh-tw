---
title: "應用程式控制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- application control
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 81eb0bcdd8c9d154f62635e7f306cefcf7a15c1b
ms.lasthandoff: 02/24/2017

---
# <a name="application-control"></a>應用程式控制
OLE 需要實際控制應用程式和其物件。 OLE 系統 Dll 必須能夠啟動及自動發行的應用程式、 協調其實際執行和修改的物件，等等。 本主題中的函式符合這些需求。 除了由 OLE 系統 Dll 呼叫，這些函式有時必須呼叫以及應用程式。  
  
### <a name="application-control"></a>應用程式控制  
  
|||  
|-|-|  
|[AfxOleCanExitApp](#afxolecanexitapp)|指示應用程式是否可以結束。|  
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|擷取應用程式的目前訊息篩選器。|  
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|擷取目前使用者控制旗標。|  
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|設定或清除使用者控制旗標。|  
|[AfxOleLockApp](#afxolelockapp)|架構的應用程式中的作用中物件的數字的全域計數遞增。|  
|[AfxOleUnlockApp](#afxoleunlockapp)|遞減架構的應用程式中的使用中物件數目計數。|  
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|在 OLE 系統登錄中註冊伺服器。|  
|[AfxOleSetEditMenu](#afxoleseteditmenu)|會實作使用者介面*typename*物件命令。|  
  
##  <a name="a-nameafxolecanexitappa--afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp  
 指示應用程式是否可以結束。  
  
```   
BOOL AFXAPI AfxOleCanExitApp(); 
```  
  
### <a name="return-value"></a>傳回值  
 如果應用程式可結束則非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果對應用程式物件有未完成的參考，則不應該結束。 全域函式 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分別會遞增和遞減應用程式物件的參考計數。 這個計數器為非零值時，應用程式不應該結束。 如果計數器是非零值，當使用者從 [系統] 功能表選擇 [關閉]，或從 [檔案] 功能表選擇 [結束] 時，應用程式的主視窗將會隱藏 (不會終結)。 架構會呼叫此函式**cframewnd:: Onclose**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAutomation #&2;](../../mfc/codesnippet/cpp/application-control_1.cpp)]  

## <a name="requirements"></a>需求  
 **標頭**: afxdisp.h 

##  <a name="a-nameafxolegetmessagefiltera--afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter  
 擷取應用程式的目前訊息篩選器。  
  
```   
COleMessageFilter* AFXAPI  AfxOleGetMessageFilter(); 
```  
  
### <a name="return-value"></a>傳回值  
 指向目前訊息篩選器的指標。  
  
### <a name="remarks"></a>備註  
 就像您會呼叫 `COleMessageFilter` 來存取目前應用程式物件一般，請呼叫這個函式來存取目前的 `AfxGetApp` 衍生物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAutomation #&3;](../../mfc/codesnippet/cpp/application-control_2.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation #&4;](../../mfc/codesnippet/cpp/application-control_3.cpp)]  

### <a name="requirements"></a>需求  
 **標頭**: afxwin.h 

##  <a name="a-nameafxolegetuserctrla--afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl  
 擷取目前使用者控制旗標。  
  
```   
BOOL  AFXAPI AfxOleGetUserCtrl(); 
```  
  
### <a name="return-value"></a>傳回值  
 如果使用者在控制應用程式則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 當使用者具有已明確開啟或建立的新文件時，應用程式是在使用者的控制之下。 如果應用程式不是由 OLE 系統 DLL 啟動，也就是說如果使用者是使用系統殼層啟動應用程式，表示仍然在使用者的控制之下。  

### <a name="requirements"></a>需求  
 **標頭**: afxdisp.h

##  <a name="a-nameafxolesetuserctrla--afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl  
 設定或清除的參考資料中說明的使用者控制旗標`AfxOleGetUserCtrl`。  
  
```  
void  AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl); 
```  
  
### <a name="parameters"></a>參數  
 *bUserCtrl*  
 指定是否要設定或清除使用者控制旗標。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式當使用者建立或載入文件，但不是會在文件會載入或建立透過間接的動作，例如從容器應用程式載入內嵌的物件。  
  
 如果您的應用程式中的其他動作應該將使用者放在控制應用程式，呼叫此函式。  

### <a name="requirements"></a>需求  
 **標頭**: afxdisp.h

##  <a name="a-nameafxolelockappa--afxolelockapp"></a><a name="afxolelockapp"></a>AfxOleLockApp  
 架構的應用程式中的作用中物件的數字的全域計數遞增。  
  
```   
void  AFXAPI  AfxOleLockApp(); 
```  
  
### <a name="remarks"></a>備註  
 架構會讓您的應用程式中作用的物件數目的計數。 `AfxOleLockApp`和`AfxOleUnlockApp`函式，會分別遞增和遞減這個計數。  
  
 使用者嘗試關閉使用中物件的應用程式-應用程式的使用中物件計數為非零值，架構會隱藏在使用者的檢視，而不是完全關閉應用程式。 `AfxOleCanExitApp`函式會指出是否可以結束應用程式。  
  
 呼叫`AfxOleLockApp`公開 OLE 介面時，如果不想要在用戶端應用程式仍在使用時終結該物件的所有物件。 也可呼叫`AfxOleUnlockApp`呼叫任何物件的解構函式中`AfxOleLockApp`建構函式。 根據預設， `COleDocument` （以及衍生類別） 會自動鎖定和解除鎖定應用程式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAutomation #&5;](../../mfc/codesnippet/cpp/application-control_4.cpp)]  

### <a name="requirements"></a>需求  
 **標頭**: afxdisp.h

##  <a name="a-nameafxoleunlockappa--afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOleUnlockApp  
 遞減架構的應用程式中使用中物件的計數。  
  
```   
void AFXAPI AfxOleUnlockApp(); 
```  
  
### <a name="remarks"></a>備註  
 請參閱`AfxOleLockApp`以取得進一步資訊。  
  
 當作用中物件的數目到達零時， **AfxOleOnReleaseAllObjects**呼叫。  
  
### <a name="example"></a>範例  
 請參閱範例[AfxOleLockApp](#afxolelockapp)。  

### <a name="requirements"></a>需求  
 **標頭**: afxdisp.h  

##  <a name="a-nameafxoleregisterserverclassa--afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass  
 此函式可讓您在 OLE 系統登錄中註冊您的伺服器。  
  
```   
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszShortTypeName,  
    LPCTSTR lpszLongTypeName,  
    OLE_APPTYPE nAppType = OAT_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 參考到伺服器的 OLE 類別識別碼。  
  
 `lpszClassName`  
 包含在伺服器物件的類別名稱的字串指標。  
  
 *lpszShortTypeName*  
 包含伺服器的物件類型，例如 「 圖表 」 的簡短名稱之字串的指標  
  
 *lpszLongTypeName*  
 字串，包含伺服器的物件類型，例如"Microsoft Excel 5.0 Chart"的完整名稱的指標  
  
 `nAppType`  
 值，取自**OLE_APPTYPE**列舉，指定 OLE 應用程式的類型。 可能的值如下所示︰  
  
- `OAT_INPLACE_SERVER`伺服器具有完整伺服器的使用者介面。  
  
- `OAT_SERVER`只有內嵌伺服器支援。  
  
- `OAT_CONTAINER`容器支援內嵌連結。  
  
- `OAT_DISPATCH_OBJECT``IDispatch`-支援的物件。  
  
 `rglpszRegister`  
 以字串表示的索引鍵和值加入至 OLE 系統登錄，如果找不到任何索引鍵的現有值的指標陣列。  
  
 `rglpszOverwrite`  
 以字串表示的索引鍵和值加入至 OLE 系統登錄，如果登錄中包含指定的索引鍵的現有值的指標陣列。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功註冊的伺服器類別;否則為 0。  
  
### <a name="remarks"></a>備註  
 大部分的應用程式可以使用**COleTemplateServer::Register**註冊應用程式的文件類型。 如果您的應用程式系統登錄格式不適用於一般的模式，您可以使用`AfxOleRegisterServerClass`進行更多控制。  
  
 登錄包含一組索引鍵和值。 `rglpszRegister`和`rglpszOverwrite`引數是以字串的指標陣列，每個組成的索引鍵和值，以分隔**NULL**字元 ( `'\0'`)。 每個這些字串可以有可置換的參數，其位置標記的字元序列`%1`透過`%5`。  
  
 符號的資料會填入，如下所示︰  
  
|符號|值|  
|------------|-----------|  
|%1|類別識別碼，格式化為字串|  
|%2|類別名稱|  
|%3|可執行檔路徑|  
|%4|簡短的型別名稱|  
|%5|Long 型別名稱|  

### <a name="requirements"></a>需求  
 **標頭**: afxdisp.h

##  <a name="a-nameafxoleseteditmenua--afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu  
 會實作使用者介面*typename*物件命令。  
  
```   
void  AFXAPI  AfxOleSetEditMenu(
    COleClientItem* pClient,  
    CMenu* pMenu,  
    UINT iMenuItem,  
    UINT nIDVerbMin,  
    UINT nIDVerbMax = 0,  
    UINT nIDConvert = 0); 
```  
  
### <a name="parameters"></a>參數  
 `pClient`  
 用戶端 OLE 項目的指標。  
  
 `pMenu`  
 要更新的功能表物件的指標。  
  
 *iMenuItem*  
 要更新的功能表項目的索引。  
  
 `nIDVerbMin`  
 命令 ID 對應至主動作。  
  
 *nIDVerbMax*  
 對應至上次動詞命令識別碼。  
  
 *nIDConvert*  
 轉換的功能表項目的 ID。  
  
### <a name="remarks"></a>備註  
 如果伺服器會辨識主要動詞命令、 功能表項目就會變成 「 動詞*typename*物件 」 和`nIDVerbMin`在使用者選擇命令時，會傳送命令。 如果伺服器會辨識的數個動詞命令，則功能表項目會變成 「 *typename*物件 」，當使用者選擇命令，列出所有動詞命令的子功能表隨即出現。 當使用者選擇動詞命令的子功能表中，`nIDVerbMin`如果選擇第一個指令動詞，傳送`nIDVerbMin`+ 1 會傳送第二個動詞時選擇、 等等。 預設`COleDocument`實作自動處理這項功能。  
  
 您必須擁有下列陳述式，在您的用戶端應用程式資源指令碼 (。RC) 檔案︰  
  
 **#include \<afxolecl.rc >**  

### <a name="requirements"></a>需求  
 **標頭**: afxole.h 

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

