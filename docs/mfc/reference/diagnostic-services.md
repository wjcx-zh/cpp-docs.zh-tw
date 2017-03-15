---
title: "診斷服務 |Microsoft 文件"
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
- diagnosis, diagnostic services
- diagnostic macros, list of general MFC
- services, diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables
- diagnostics, diagnostic functions and variables
- diagnostics, list of general MFC
- diagnosis, diagnostic functions and variables
- diagnosis, list of general MFC
- general diagnostic macros in MFC
- diagnostic macros
- diagnostic services
- object diagnostic functions in MFC
- diagnostics, diagnostic services
- diagnostic functions and variables
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 86fe366a4d7863fb9339b7b5a9f880103876de33
ms.lasthandoff: 02/24/2017

---
# <a name="diagnostic-services"></a>診斷服務
MFC 程式庫提供許多診斷服務，可讓您更輕鬆地對程式進行偵錯。 這些診斷服務包含巨集和全域函式，可讓您追蹤程式的記憶體配置、在執行階段傾印物件的內容，以及在執行階段列印偵錯訊息。 診斷服務的巨集和全域函式可分為下列分類：  
  
-   一般診斷巨集  
  
-   一般診斷函式和變數  
  
-   物件診斷函式  
  
 這些巨集和函式可供使用的所有類別都衍生自`CObject`MFC 偵錯和發行版本中。 不過，所有除了`DEBUG_NEW`和**確認**不執行任何動作的發行版本中。  
  
 在偵錯程式庫中，所有配置的記憶體區塊都會以一系列「保護位元組」(Guard Byte) 來提供支援。 如果這些位元組受到錯誤記憶體寫入的干擾，則診斷常式可能會回報問題。 如果您在實作檔中包含此行：  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 在實作檔中，所有呼叫**新**會儲存在記憶體配置中發生了檔名和行數。 函式[CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince)會顯示此額外資訊，可讓您找出記憶體流失。 參考的類別也[CDumpContext](../../mfc/reference/cdumpcontext-class.md)如需有關診斷輸出。  
  
 此外，C 執行階段程式庫也支援一組可用來偵錯應用程式的診斷函式。 如需詳細資訊，請參閱[偵錯常式](../../c-runtime-library/debug-routines.md)在執行階段程式庫參考。  
  
### <a name="mfc-general-diagnostic-macros"></a>MFC 一般診斷巨集  
  
|||  
|-|-|  
|[判斷提示](#assert)|列印一則訊息，則會中止程式，如果指定的運算式評估為**FALSE**中的程式庫的偵錯版本。|  
|[ASSERT_KINDOF](#assert_kindof)|測試物件是指定類別的物件，還是衍生自指定類別之類別的物件。|  
|[ASSERT_VALID](#assert_valid)|測試物件的內部有效性藉由呼叫其`AssertValid`成員函式; 通常覆寫從`CObject`。|  
|[DEBUG_NEW](#debug_new)|提供偵錯模式中所有物件配置的檔案名稱和行號，以協助找出記憶體流失的問題。|  
|[DEBUG_ONLY](#debug_only)|類似於**ASSERT**但不會測試的運算式，值應該只在偵錯模式中執行的程式碼很有用。|  
|[TRACE](#trace)|提供`printf`-要在程式庫的偵錯版本的功能。|  
|[確認](#verify)|類似於**ASSERT**但評估程式庫也與偵錯版本的發行版本中的運算式。|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 一般診斷變數和函式  
  
|||  
|-|-|  
|[afxDump](#afxdump)|傳送的全域變數[CDumpContext](../../mfc/reference/cdumpcontext-class.md)偵錯工具的 [輸出] 視窗或偵錯終端機的資訊。|  
|[afxMemDF](#afxmemdf)|全域變數，可控制偵錯記憶體配置器的行為。|  
|[AfxCheckError](#afxcheckerror)|用來測試傳遞的全域變數**SCODE**查看如果它是錯誤，如果是的話，則會擲回適當的錯誤。|  
|[AfxCheckMemory](#afxcheckmemory)|檢查目前配置之所有記憶體的完整性。|  
|[AfxDump](#cdumpcontext_in_mfc_)|如果在偵錯工具中呼叫，則會一面進行偵錯，一面傾印物件的狀態。|  
|[AfxDumpStack](#afxdumpstack)|產生目前堆疊的映像。 這個函式一律會以靜態方式連結。|  
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|啟用記憶體流失傾印。|  
|[AfxEnableMemoryTracking](#afxenablememorytracking)|開啟和關閉記憶體追蹤。|  
|[AfxIsMemoryBlock](#afxismemoryblock)|確認已適當地配置記憶體區塊。|  
|[AfxIsValidAddress](#afxisvalidaddress)|確認記憶體位址範圍落在程式的範圍內。|  
|[AfxIsValidString](#afxisvalidstring)|判斷字串指標是否有效。|  
|[AfxSetAllocHook](#afxsetallochook)|允許對每個記憶體配置呼叫函式。|  
  
### <a name="mfc-object-diagnostic-functions"></a>MFC 物件診斷函式  
  
|||  
|-|-|  
|[AfxDoForAllClasses](#afxdoforallclasses)|對所有指定的函式`CObject`-衍生的類別支援執行階段型別檢查。|  
|[AfxDoForAllObjects](#afxdoforallobjects)|對所有指定的函式`CObject`-衍生物件所配置的**新**。|  
  
##  <a name="a-nameasserta--assert"></a><a name="assert"></a>判斷提示
 會評估其引數。  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>參數  
 `booleanExpression`  
 指定評估為非零值則為 0 的運算式 （包括指標值）。  
  
### <a name="remarks"></a>備註  
 如果結果為 0，巨集會列印診斷訊息，並中止程式。 如果條件為非零，就沒有作用。  
  
 診斷資訊的格式如下  
  
 `assertion failed in file <name> in line <num>`  
  
 其中*名稱*是來源檔案的名稱和*num*是原始程式檔中失敗的判斷提示行號。  
  
 在發行版本的 MFC 中， **ASSERT**不會評估運算式，因此並不會中斷程式。 如果必須不論環境中評估運算式，使用**確認**巨集取代**ASSERT**。  
  
> [!NOTE]
>  此函式是只能在 MFC 的偵錯版本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&44;](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameassertkindofa--assertkindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF  
 這個巨集判斷提示所指向的物件為指定的類別的物件，或從指定的類別衍生類別的物件。  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>參數  
 *類別名稱*  
 名稱`CObject`-衍生的類別。  
  
 *pobject*  
 類別物件的指標。  
  
### <a name="remarks"></a>備註  
 *Pobject*參數應該是物件的指標，而且可以是**const**。 指向的物件和類別必須支援`CObject`執行階段類別資訊。 做為範例，以確保`pDocument`是物件的指標`CMyDoc`類別或任何衍生項目，您可以撰寫程式碼︰  
  
 [!code-cpp[NVC_MFCDocView #&194;](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 使用`ASSERT_KINDOF`巨集就是撰寫程式碼相同︰  
  
 [!code-cpp[NVC_MFCDocView #&195;](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 此函數僅適用於類別宣告為具有 [DECLARE_DYNAMIC] (執行的時間-物件-模型-services.md #declare_dynamic 或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集。  
  
> [!NOTE]
>  此函式是只能在 MFC 的偵錯版本。  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameassertvalida--assertvalid"></a><a name="assert_valid"></a>ASSERT_VALID  
 使用測試物件的內部狀態的有效性的相關假設。  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>參數  
 `pObject`  
 指定的物件的類別，衍生自`CObject`具有覆寫版本的`AssertValid`成員函式。  
  
### <a name="remarks"></a>備註  
 `ASSERT_VALID`呼叫`AssertValid`物件的成員函式傳遞做為引數。  
  
 在發行版本的 MFC 中，`ASSERT_VALID`不做任何動作。 在偵錯版本中，它會驗證指標，檢查**NULL**，而且會呼叫物件的自己`AssertValid`成員函式。 如果其中任何一項測試失敗，將警示訊息會顯示在相同的方式來[ASSERT](#assert)。  
  
> [!NOTE]
>  此函式是只能在 MFC 的偵錯版本。  
  
 如需詳細資訊和範例，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&19;](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-namedebugnewa--debugnew"></a><a name="debug_new"></a>DEBUG_NEW  
 協助尋找記憶體流失。  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>備註  
 您可以使用`DEBUG_NEW`通常會使用您程式中的所有**新**運算子來配置堆積存放區。  
  
 偵錯模式中 (當**_DEBUG**定義符號)，`DEBUG_NEW`會持續追蹤的每個物件所配置的檔名和行數。 然後，當您使用[CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince)成員函式，以配置每個物件`DEBUG_NEW`上顯示的檔名和行號配置位置。  
  
 若要使用`DEBUG_NEW`，將下列指示詞插入至原始程式檔︰  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 一旦您插入此指示詞，前置處理器會插入`DEBUG_NEW`無論您使用**新**，MFC 就會進行其餘。 當您編譯程式的發行版本`DEBUG_NEW`解析成簡單**新**不產生作業和檔名和行號資訊。  
  
> [!NOTE]
>  在先前版本的 MFC （4.1 及更早版本），您必須將`#define`呼叫的所有陳述式之後的陳述式`IMPLEMENT_DYNCREATE`或`IMPLEMENT_SERIAL`巨集。 這已不再需要。  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-namedebugonlya--debugonly"></a><a name="debug_only"></a>DEBUG_ONLY  
 在偵錯模式中 (當**_DEBUG**定義符號)，`DEBUG_ONLY`評估其引數。  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>備註  
 在發行組建， **DEBUG_ONLY**不會評估其引數。 當您的程式碼，都應該只在偵錯組建中執行，這非常有用。  
  
 `DEBUG_ONLY`巨集就相當於周圍*運算式*與**#ifdef _DEBUG**和`#endif`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&32;](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-nametracea--trace"></a><a name="trace"></a>追蹤  
 將指定的字串傳送至目前的應用程式的偵錯工具。  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>備註  
 請參閱[ATLTRACE2](http://msdn.microsoft.com/library/467ff555-e7a5-4f94-bdd9-50ee27ab9986)的說明**追蹤**。 **追蹤**和`ATLTRACE2`有相同的行為。  
  
 在 MFC 的偵錯版本中，這個巨集，請將目前的應用程式的偵錯工具指定的字串。 發行組建中，這個巨集將編譯為無 （不會產生程式碼完全）。  
  
 如需詳細資訊，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-nameverifya--verify"></a><a name="verify"></a>確認  
 在 MFC 的偵錯版本，會評估其引數。  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>參數  
 `booleanExpression`  
 指定評估為非零值則為 0 的運算式 （包括指標值）。  
  
### <a name="remarks"></a>備註  
 如果結果為 0，巨集會列印診斷訊息，並中止程式。 如果條件為非零，就沒有作用。  
  
 診斷資訊的格式如下  
  
 `assertion failed in file <name> in line <num>`  
  
 其中*名稱*是原始程式檔的名稱和*num*是原始程式檔中失敗的判斷提示行號。  
  
 在發行版本的 MFC 中，**確認**會評估運算式，但不會列印或中斷程式。 例如，如果運算式是函式呼叫，將會進行呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&198;](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-namecdumpcontextinmfca--afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc_"></a>afxDump (MFC 中的 CDumpContext)  
 提供在您的應用程式的基本物件傾印功能。  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>備註  
 `afxDump`預先定義的[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件，可讓您傳送`CDumpContext`偵錯工具的 [輸出] 視窗或偵錯終端機的資訊。 一般而言，您提供`afxDump`做為參數`CObject::Dump`。  
  
 在 Windows NT 和所有的 Windows 版本，`afxDump`偵錯您的應用程式時，輸出會傳送至 Visual c + + 的偵錯輸出視窗。  
  
 只在 MFC 的偵錯版本中定義此變數。 如需有關`afxDump`，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&23;](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-nameafxmemdfa--afxmemdf"></a><a name="afxmemdf"></a>afxMemDF  
 這個變數存取從偵錯工具或您的程式，並可讓您調整配置診斷。  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>備註  
 `afxMemDF`可以是下列值所指定的列舉型別`afxMemDF`:  
  
- **allocMemDF**開啟偵錯的配置器 （偵錯程式庫中的預設值）。  
  
- **delayFreeMemDF**延遲釋放記憶體。 雖然您的程式釋放記憶體區塊，配置器不會傳回該記憶體基礎作業系統。 這會在程式的最大記憶體負荷。  
  
- **checkAlwaysMemDF**呼叫`AfxCheckMemory`每次配置或釋放記憶體。 這會將大幅降低記憶體配置和解除配置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&30;](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-nameafxcheckerrora--afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError  
 此函式會測試傳遞**SCODE**是否發生錯誤。  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>備註  
 如果是錯誤，函式會擲回例外狀況。 如果傳入`SCODE`是**E_OUTOFMEMORY**，函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)藉由呼叫[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 否則，函式會擲回[COleException](../../mfc/reference/coleexception-class.md)藉由呼叫[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。  
  
 這個函式可用來檢查對應用程式中 OLE 函式呼叫的傳回值。 藉由在應用程式中以此函式測試傳回值，您可以用最少的程式碼因應錯誤狀況。  
  
> [!NOTE]
>  這個函式在偵錯和非偵錯組建中具有相同的效果。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&33;](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h

##  <a name="a-nameafxcheckmemorya--afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheckMemory  
 此函式會驗證可用記憶體集區，並會列印錯誤訊息所需。  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>傳回值  
 如果沒有記憶體錯誤，為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果函式偵測到記憶體損毀，就會列印任何動作。  
  
 檢查所有在堆積上目前配置的記憶體區塊，包括所配置的**新**但無法直接呼叫基礎的記憶體配置器所配置的這類`malloc`函式或**GlobalAlloc** Windows 函式。 如果發現任何區塊是已損毀，則訊息會列印至偵錯工具的輸出。  
  
 如果您要加入線條  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 在程式模組中，則後續呼叫`AfxCheckMemory`顯示的檔名和行號配置的記憶體位置。  
  
> [!NOTE]
>  如果您的模組包含一或多個類別實作之可序列化，則您必須將此`#define`最後一個之後的行`IMPLEMENT_SERIAL`巨集呼叫。  
  
 此函式只適用於 MFC 的偵錯版本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCObjectSample #&26;](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h  
 
##  <a name="a-namemfca--afxdump-mfc"></a><a name="mfc_"></a>AfxDump (MFC)  
 呼叫此函式在偵錯工具傾印進行偵錯時的物件狀態中。  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>參數  
 `pOb`  
 從衍生類別的物件指標`CObject`。  
  
### <a name="remarks"></a>備註  
 **AfxDump**呼叫物件的`Dump`成員函式，並將所指定的位置資訊`afxDump`變數。 **AfxDump**僅適用於 MFC 的偵錯版本。  
  
 您的程式碼不應該呼叫**AfxDump**，但應該改為呼叫`Dump`成員函式的適當的物件。  
  
##  <a name="a-nameafxdumpstacka--afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack  
 此全域函式可以用來產生目前的堆疊的映像。  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>參數  
 *dwTarget*  
 表示傾印的輸出目標。 可能的值，可以使用位元 OR 結合 ( **|**) 運算子，如下︰  
  
- **AFX_STACK_DUMP_TARGET_TRACE**傳送輸出藉由[追蹤](#trace)巨集。 **追蹤**巨集只能偵錯組建中產生輸出，則在發行的組建會產生任何輸出。 此外，**追蹤**可以重新導向至偵錯工具以外的其他目標。  
  
- **AFX_STACK_DUMP_TARGET_DEFAULT**傳送傾印預設目標的輸出。 偵錯組建中，會輸出至**追蹤**巨集。 在發行組建中，會輸出至剪貼簿。  
  
- **AFX_STACK_DUMP_TARGET_CLIPBOARD**將輸出傳送到只在剪貼簿。 將資料放在剪貼簿以純文字使用**CF_TEXT**剪貼簿格式。  
  
- **AFX_STACK_DUMP_TARGET_BOTH**傳送輸出至剪貼簿和**追蹤**巨集，同時。  
  
- **AFX_STACK_DUMP_TARGET_ODS**利用 Win32 函式，將輸出傳送至偵錯工具直接**OutputDebugString()**。 這個選項會產生偵錯工具輸出，在這兩個偵錯，偵錯工具附加至處理序時，發行組建。 **AFX_STACK_DUMP_TARGET_ODS**永遠會到達偵錯工具 （如果它是），而且無法重新導向。  
  
### <a name="remarks"></a>備註  
 下列範例會反映呼叫所產生的輸出一行`AfxDumpStack`從 MFC 對話方塊應用程式中的按鈕處理常式︰  
  
 `=== begin AfxDumpStack output ===`  
  
 `00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes`  
  
 `0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes`  
  
 `0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,`  
  
 `unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct AFX_CMDHANDLE`  
  
 `0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes`  
  
 `00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes`  
  
 `00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned`  
  
 `int,long) + 312 bytes`  
  
 `00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned`  
  
 `int,unsigned int,long,long *) + 83 bytes`  
  
 `00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned`  
  
 `int,unsigned int,long) + 46 bytes`  
  
 `004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct`  
  
 `HWND__ *,unsigned int,unsigned int,long) + 237 bytes`  
  
 `00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned`  
  
 `int,unsigned int,long) + 129 bytes`  
  
 `BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes`  
  
 `BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes`  
  
 `=== end AfxDumpStack() output ===`  
  
 在上述輸出中的每一行，表示最後一個函式呼叫的函式呼叫時，並呼叫的函式原型包含模組的完整路徑名稱的位址。 如果函式呼叫堆疊上的不會發生在正確的函式的位址，就會顯示的位元組位移。  
  
 例如下, 表說明上述輸出中的第一行︰  
  
|輸出|說明|  
|------------|-----------------|  
|`00427D55:`|最後一個函式呼叫的傳回位址。|  
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函式呼叫的模組完整路徑名稱。|  
|`void AfxDumpStack(unsigned long)`|呼叫函式原型。|  
|`+ 181 bytes`|以位元組為單位，從函式原型的位址位移 (在此情況下， `void AfxDumpStack(unsigned long)`) 傳回的位址 (在此情況下， `00427D55`)。|  
  
 `AfxDumpStack`提供偵錯和非偵錯版本的 MFC 程式庫。不過，函式會一律連結以靜態方式，即使可執行檔使用 MFC 的共用 dll。 在共用程式庫實作中，函式 MFCS42 中找到。LIB 程式庫 （與變種）。  
  
 若要成功使用此函式︰  
  
-   IMAGEHLP 檔案。DLL 必須位於您的路徑。 如果您沒有此 DLL，函式會顯示錯誤訊息。 請參閱[影像協助程式庫](http://msdn.microsoft.com/library/windows/desktop/ms680321)IMAGEHLP 所提供的函式集上的資訊。  
  
-   已在堆疊框架的模組必須包含偵錯資訊。 如果它們不包含偵錯資訊，函式仍會產生堆疊追蹤，但較不詳細的追蹤。  
### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxenablememoryleakdumpa--afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump  
 啟用和停用 `AFX_DEBUG_STATE` 解構函式中的記憶體流失傾印。  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDump`  
 `TRUE` 表示已啟用記憶體流失傾印；`FALSE` 則表示已停用記憶體流失傾印。  
  
### <a name="return-value"></a>傳回值  
 此旗標先前的值。  
  
### <a name="remarks"></a>備註  
 當應用程式卸載 MFC 程式庫時，MFC 程式庫會檢查記憶體流失。 此時，任何記憶體遺漏會提報給使用者透過**偵錯**視窗[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]。  
  
 如果您的應用程式在 MFC 程式庫之前先載入另一個程式庫，系統會將該程式庫中的一些記憶體配置誤報為記憶體流失。 因為 MFC 程式庫發生記憶體流失誤報的情況，這些誤報可能會導致您的應用程式關閉速度很慢。 在這種情況下，請使用 `AfxEnableMemoryLeakDump` 以停用記憶體流失傾印。  
  
> [!NOTE]
>  如果您使用這個方法來關閉記憶體流失傾印，就不會收到應用程式中有效的記憶體流失報告。 因此，僅有當您確信記憶體流失報告包含誤報的記憶體流失，才建議使用這個方法。  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxenablememorytrackinga--afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking  
 MFC 偵錯版本通常會啟用診斷追蹤的記憶體。  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>參數  
 *bTrack*  
 此值設定為**TRUE**開啟記憶體追蹤。**FALSE**會關閉。  
  
### <a name="return-value"></a>傳回值  
 追蹤啟用旗標先前的設定。  
  
### <a name="remarks"></a>備註  
 若要停用追蹤，您就可以正確地配置區塊的程式碼的區段上使用此函式。  
  
 如需有關`AfxEnableMemoryTracking`，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。  
  
> [!NOTE]
>  此函式只適用於 MFC 的偵錯版本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&24;](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxismemoryblocka--afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock  
 測試以確定它代表診斷版本所配置的目前作用中的記憶體區塊的記憶體位址**新**。  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `p`  
 要測試記憶體區塊的指標。  
  
 `nBytes`  
 包含記憶體區塊，以位元組為單位的長度。  
  
 `plRequestNumber`  
 指向**長**會填入記憶體區塊的配置順序編號，或如果它不代表目前使用的記憶體區塊為零的整數。  
  
### <a name="return-value"></a>傳回值  
 非零，如果目前已配置的記憶體區塊，而且長度是正確的。否則為 0。  
  
### <a name="remarks"></a>備註  
 它也會檢查指定的大小，針對原始配置的大小。 如果此函數會傳回非零，就會傳回配置順序編號`plRequestNumber`。 這個數字代表相對於所有其他已配置區塊的順序**新**配置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&27;](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxisvalidaddressa--afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAddress  
 測試以確保它包含程式的記憶體空間內的任何記憶體位址。  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>參數  
 `lp`  
 要測試的記憶體位址的指標。  
  
 `nBytes`  
 包含要測試記憶體的位元組數目。  
  
 *bReadWrite*  
 指定的記憶體是用來讀取和寫入 ( **TRUE**) 或只讀取 ( **FALSE**)。  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建中，如果指定的記憶體區塊為非零當中完全程式的記憶體空間。否則為 0。  
  
 在非偵錯組建中，為非零的 if`lp`不是 NULL，否則為 0。  
  
### <a name="remarks"></a>備註  
 位址不會套用至所配置的區塊**新**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&28;](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxisvalidstringa--afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString  
 您可以使用此函式來判斷字串的指標是否有效。  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 要測試的指標。  
  
 `nLength`  
 指定要測試，以位元組為單位的字串長度。 值的人員-「&1; 表示會以 null 結束的字串。  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建中，非零，如果指定的指標指向的字串，指定的大小。否則為 0。  
  
 在非偵錯組建中，為非零的 if`lpsz`不是 NULL，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&29;](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxsetallochooka--afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHook  
 設定每個記憶體區塊配置之前，可讓指定的函式呼叫的攔截。  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>參數  
 *pfnAllocHook*  
 指定要呼叫的函式的名稱。 請參閱備註的配置函式的原型。  
  
### <a name="return-value"></a>傳回值  
 非零，如果您想要允許配置;否則為 0。  
  
### <a name="remarks"></a>備註  
 Mfc 程式庫的偵錯記憶體配置器可以呼叫使用者定義之 hook 函式，讓使用者以監視記憶體配置，並控制是否允許配置。 配置攔截函式的原型，如下所示︰  
  
 **BOOL AFXAPI AllocHook( size_t** `nSize`**, BOOL** `bObject`**, LONG** `lRequestNumber` **);**  
  
 `nSize`  
 建議的記憶體配置的大小。  
  
 `bObject`  
 **TRUE**配置時的`CObject`-衍生物件，否則為**FALSE**。  
  
 `lRequestNumber`  
 記憶體配置順序編號。  
  
 請注意， **AFXAPI**呼叫慣例隱含被呼叫端必須從堆疊移除參數。  

### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxdoforallclassesa--afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses  
 呼叫指定之反覆項目函式的所有可序列化`CObject`-應用程式的記憶體空間中衍生類別。  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>參數  
 `pfn`  
 針對每個類別呼叫的反覆項目函式的指標。 函式引數是一個指向`CRuntimeClass`物件和函式的呼叫端提供的額外資料的 void 指標。  
  
 `pContext`  
 呼叫端可以提供給反覆項目函式的選擇性資料點。 此指標可以是**NULL**。  
  
### <a name="remarks"></a>備註  
 可序列化`CObject`-衍生的類別是使用衍生的類別`DECLARE_SERIAL`巨集。 將指標傳遞至`AfxDoForAllClasses`中`pContext`會傳遞至指定的反覆項目函式每次呼叫時。  
  
> [!NOTE]
>  此函式只適用於 MFC 的偵錯版本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&113;](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections #&114;](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>需求  
 **標頭：** afx.h 

##  <a name="a-nameafxdoforallobjectsa--afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects  
 執行指定的反覆項目函式的所有物件都衍生自`CObject`以已配置**新**。  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>參數  
 `pfn`  
 反覆項目要執行函式的每個物件的指標。 函式引數是一個指向`CObject`和 void 指標至函式的呼叫端提供的額外資料。  
  
 `pContext`  
 呼叫端可以提供給反覆項目函式的選擇性資料點。 此指標可以是**NULL**。  
  
### <a name="remarks"></a>備註  
 不會列舉堆疊全域或內嵌的物件。 將指標傳遞至`AfxDoForAllObjects`中`pContext`會傳遞至指定的反覆項目函式每次呼叫時。  
  
> [!NOTE]
>  此函式只適用於 MFC 的偵錯版本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&115;](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections&116;](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
