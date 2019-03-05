---
title: ATL 類別和結構 |Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 561d6cb41ca066f5a2435b4eb1e8710ccaa99ea1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265565"
---
# <a name="atl-classes-and-structs"></a>ATL 類別和結構

Active Template Library (ATL) 包含下列類別和結構。 若要依分類尋找特定的類別，請參閱[ATL 類別概觀](../../atl/atl-class-overview.md)。

|類別 / 結構|描述|標頭檔|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|包含用於轉譯成各種不同的目標，例如印表機、 中繼檔或 ActiveX 控制項的資訊。|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|包含在 ATL 中的視窗化程式碼中的類別執行個體資料|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|使用任何使用 ATL 的專案|atlbase.h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|ATL 中的 COM 相關程式碼使用| atlbase.h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|包含用來描述在分配介面上的方法或屬性的型別資訊。|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|包含每個 ATL 模組所使用的資料。|atlbase.h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|ATL 中的視窗化程式碼使用|atlbase.h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|這個類別會使用字串轉換巨集 CA2TEX CT2AEX 和 typedef CA2A。|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|這個類別會使用字串轉換巨集 CA2CTEX CT2CAEX 和 typedef CA2CA。|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|這個類別會使用字串轉換巨集 CA2TEX、 CA2CTEX、 CT2WEX，和 CT2CWEX 和 typedef CA2W。|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|這個類別是存取權杖的包裝函式。|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|這個類別是 ACL （存取控制清單） 結構的包裝函式。|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|此範本用來包裝重新定義傳址 (address-of) 運算子的類別，以傳回物件位址以外的內容。|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|這個類別會實作陣列物件。|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|這個類別會實作在執行緒集區的 apartment model COM 伺服器。|atlbase.h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|這個類別提供方法實作在執行緒集區的 apartment model COM 伺服器。|atlbase.h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|這個類別是在每個 ATL 專案中具現化。|atlcore.h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|這個類別會實作 COM 伺服器模組。|atlbase.h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|這個類別提供支援偵錯介面。|atlbase.h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|此類別代表模組的 dll。|atlbase.h|
|[CAtlException](../../atl/reference/catlexception-class.md)|這個類別會定義 ATL 例外狀況。|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|此類別代表應用程式的模組。|atlbase.h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|這個類別會提供 Windows 精簡型包裝函式的檔案處理 API。|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|此類別代表記憶體對應檔案，加入的方法中的轉換運算子[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|此類別代表的記憶體對應檔。|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|這個類別提供方法來建立和管理的清單物件。|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|這個類別提供方法來建立和管理一個 map 物件。|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|這個類別提供數個 ATL 模組類別所使用的方法。|atlbase.h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|這個類別會實作 「 ATL 模組。|atlbase.h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|這個類別是視窗的 ATL 的實作會放在 Shell for Rich Preview 提供的主視窗。|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|這個類別會實作一項服務。|atlbase.h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|這個類別提供建立和使用的暫存檔案的方法。|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|這個類別會提供核心交易管理員 (KTM) 的函式的包裝函式。|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|這個類別提供 ATL 視窗化元件的支援。|atlbase.h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|此類別代表智慧型指標物件。|atlbase.h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|建構的智慧型指標陣列時，這個類別會提供有用的方法。|atlbase.h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|建立智慧型指標的集合時，這個類別會提供方法、 靜態的函式和實用的 typedef。|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|建構的智慧型指標清單時，這個類別會提供有用的方法。|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|此類別代表使用新的向量的智慧型指標物件和 delete 運算子。|atlbase.h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|這個類別提供方法、 靜態的函式和建立使用新的向量的智慧型指標的集合和 delete 運算子時很有用的 typedef。|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|這個類別會實作裝載 ActiveX 控制項對話方塊 （強制回應或非強制回應）。|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|這個類別提供方法，以操作裝載 ActiveX 控制項的視窗。|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|這個類別提供方法，以操作視窗裝載 ActiveX 控制項，也有提供裝載授權的 ActiveX 控制項的支援。|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|這個類別會實作 `IBindStatusCallback` 介面。|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|這個類別會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)彙總的物件。|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|這個類別提供方法來管理使用 COM 記憶體常式的記憶體。|atlbase.h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|這個類別會提供支援，來管理執行緒集區的 EXE 模組中的 apartment。|atlbase.h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|這個類別提供方法來取得和釋放重要區段物件的擁有權。|atlcore.h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|ATL 7.0 截至`CComAutoThreadModule`已淘汰： 請參閱 < [ATL 模組](../../atl/atl-module-classes.md)如需詳細資訊。|atlbase.h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|這個類別是 Bstr 的包裝函式。|atlbase.h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|這個類別會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)撕下介面。|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|這個類別會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面。|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|這個類別會實作[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)介面。|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|這個類別會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面，並允許在多個 apartment 中建立的物件。|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|這個類別衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)並用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|這個類別提供方法來建立類別的執行個體，並取得其屬性。|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|這個類別會提供實作複合控制項所需的方法。|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|這個類別會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)委派給擁有者物件，以`IUnknown`。|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|這個類別提供方法來建立及管理 ATL 的控制項。|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|這個類別提供方法來建立及管理 ATL 的控制項。|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|這個類別提供方法來取得和釋放重要區段物件的擁有權。|atlcore.h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|這個類別會提供鎖定和解除鎖定重要區段物件的方法。|atlbase.h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|這個類別會具有方法和運算子建立及管理 CURRENCY 物件。|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|此類別會儲存在陣列`IUnknown`指標。|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|這個類別會定義 COM 列舉值物件的陣列為基礎。|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|這個類別會提供要列舉的項目儲存在陣列中的 COM 列舉程式介面的實作。|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|這個類別會定義 c + + 標準程式庫集合為基礎的 COM 列舉值物件。|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|這個類別會提供相同的方法， [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)但並不會提供重要的區段。|atlcore.h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|這個類別提供方法來處理介面指標和全域介面表 (GIT)。|atlbase.h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 COM 記憶體配置函式。|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|用來管理堆積指標的智慧型指標類別。|atlbase.h|
|[CComModule](../../atl/reference/ccommodule-class.md)|ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組](../../atl/atl-module-classes.md)如需詳細資訊。|atlbase.h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|這個類別提供安全執行緒方法遞增和遞減變數的值。|atlbase.h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|這個類別會提供安全執行緒方法遞增和遞減變數的值，而不需要重要區段鎖定或解除鎖定功能。|atlbase.h|
|[CComObject](../../atl/reference/ccomobject-class.md)|這個類別會實作`IUnknown`非彙總的物件。|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|此類別會管理模組包含的參考計數程式`Base`物件。|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|這個類別會實作`IUnknown`的非彙總的物件，但是不會遞增模組鎖定計數的建構函式。|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|此 typedef [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)樣板化預設的執行緒模型的伺服器上。|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|這個類別提供方法來處理非彙總與彙總物件的物件參考計數管理。|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|這個類別建立暫存的 COM 物件，並為它提供的架構實作`IUnknown`。|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|這個類別會實作`IUnknown`彙總或非彙總物件。|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|用來管理 COM 介面指標的智慧型指標類別。|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|這個類別會使用以 COM 為基礎的記憶體常式的智慧型指標類別提供基礎。|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|用來管理 COM 介面指標的智慧型指標類別。|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|當建立 COM 介面指標的集合，這個類別會提供方法、 靜態的函式和實用的 typedef。|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|這個類別是包裝函式`SAFEARRAY Data Type`結構。|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|這個類別是包裝函式`SAFEARRAYBOUND`結構。|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|此類別會管理類別選取執行緒[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。|atlbase.h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|這個類別提供方法遞增和遞減變數的值。|atlbase.h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|這個類別會實作分割的介面。|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|這個類別會儲存`IUnknown`指標，旨在用於做為參數[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類別。|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|這個類別會包裝 VARIANT 型別，提供成員，表示儲存的資料類型。|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|這個類別會實作包含在另一個物件的視窗。|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|這個類別提供方法來管理使用 CRT 記憶體常式的記憶體。|atlcore.h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 CRT 堆積函式。|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|這個類別是 DACL （判別存取控制清單） 結構的包裝函式。|atlsecurity.h|
|[CDebugReportHook 類別](../../atl/reference/cdebugreporthook-class.md)|您可以使用這個類別，將偵錯報表傳送給具名管道。|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|這個類別提供兩個靜態函式之間大寫和小寫字元轉換。|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|這個類別會提供預設項目比較函式。|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|這個類別會提供預設方法和函式的集合類別。|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|這個類別提供靜態函式來計算雜湊值。|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|這個類別提供方法來建立非強制回應或非強制回應對話方塊。|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|這個類別提供支援動態鏈結的訊息對應的方法。|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|這個類別的集合類別來移動、 複製、 相較之下，和雜湊作業提供方法和函式。|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|這個類別會提供預設的複製，並移動集合類別的方法。|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|這個類別提供方法來通知控制項屬性變更有關容器的接收器。|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 全域堆積函式。|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|這個類別提供建立及使用控制代碼物件的方法。|atlbase.h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|用來管理堆積指標的智慧型指標類別。|atlcore.h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|這個類別會構成智慧堆積指標的數個類別的基礎。|atlcore.h|
|[CHeapPtrElementTraits 類別](../../atl/reference/cheapptrelementtraits-class.md)|建立集合的堆積指標時，這個類別會提供方法、 靜態的函式和實用的 typedef。|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|建構一份堆積指標時，這個類別會提供有用的方法。|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供增強的點陣圖支援，包括載入和儲存 JPEG、 GIF、 BMP、 和可攜式網路圖形 (PNG) 格式的映像的能力。|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|建構 COM 介面指標的陣列時，這個類別會提供有用的方法。|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|建構 COM 介面指標的清單時，這個類別會提供有用的方法。|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 本機堆積函式。|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|這個類別可讓物件的訊息對應至另一個物件來存取。|atlwin.h|
|[CNonStatelessWorker 類別](../../atl/reference/cnonstatelessworker-class.md)|會從執行緒集區接收要求，並將其傳遞至會建立並終結背景工作物件中每個要求。|atlutil.h|
|[CNoWorkerThread 類別](../../atl/reference/cnoworkerthread-class.md)|使用這個類別做為引數`MonitorClass`範本參數快取類別，如果您想要停用動態快取維護。|atlutil.h|
|[CPathT 類別](../../atl/reference/cpatht-class.md)|此類別代表的路徑。|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|這個類別會提供預設方法，集合類別的函式是由基本資料類型所組成。|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|此類別代表私用物件安全性描述元物件。|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|此類別代表一使用紅黑二進位樹狀目錄的對應結構。|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|此類別代表對應的結構，可與多個值，並使用紅黑二進位樹狀目錄相關聯的每個索引鍵。|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|這個類別提供方法來建立和使用紅黑樹狀結構。|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|這個類別提供方法，以操作系統登錄中的項目。|atlbase.h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|這個類別會提供建立函式的 CRT 往來文章。 如果執行緒會使用 CRT 函式，請使用這個類別。|atlbase.h|
|[CSacl](../../atl/reference/csacl-class.md)|這個類別是 SACL （系統存取控制清單） 結構的包裝函式。|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|這個類別是精簡型包裝函式`SECURITY_ATTRIBUTES`結構。|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|這個類別是包裝函式`SECURITY_DESCRIPTOR`結構。|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|這個類別是包裝函式`SID`（安全性識別碼） 結構。|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|這個類別提供方法來管理簡單的陣列。|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|這個類別是 helper [CSimpleArray](../../atl/reference/csimplearray-class.md)類別。|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|這個類別是 helper [CSimpleArray](../../atl/reference/csimplearray-class.md)類別。|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|這個類別會實作基本的強制回應對話方塊。|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|這個類別會提供簡單的對應陣列的支援。|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|這個類別是 helper [CSimpleMap](../../atl/reference/csimplemap-class.md)類別。|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|這個類別是 helper [CSimpleMap](../../atl/reference/csimplemap-class.md)類別。|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|這個類別提供方法實作的嵌入式管理單元節點物件。|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|這個類別提供方法實作嵌入式管理單元 屬性頁面物件。|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|這個類別提供方法來支援內建屬性的值。|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|這個類別會提供使用儲存的集合類別的靜態函式`CString`物件。|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|這個類別提供靜態的函式與儲存在集合類別物件的字串。 類似於[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但是執行不區分大小寫的比較。|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|這個類別提供靜態的函式與儲存在集合類別物件的字串。 做為參考未處理的字串物件。|atlcoll.h|
|[CThreadPool 類別](../../atl/reference/cthreadpool-class.md)|這個類別會提供處理的工作項目佇列的背景工作執行緒集區。|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|這個類別是包裝函式`TOKEN_GROUPS`結構。|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|這個類別是包裝函式`TOKEN_PRIVILEGES`結構。|atlsecurity.h|
|[CUrl 類別](../../atl/reference/curl-class.md)|這個類別表示的 URL。 它可讓您管理的獨立於其他 URL 的每個項目，是否剖析現有的 URL 字串，或從從頭開始建置字串。|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|這個類別會使用字串轉換巨集 CT2AEX、 CW2TEX、 CW2CTEX，和 CT2CAEX 和 typedef CW2A。|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|這個類別會使用字串轉換巨集 CW2CTEX CT2CWEX 和 typedef CW2CW。|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|這個類別會使用字串轉換巨集 CW2TEX CT2WEX 和 typedef CW2W。|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 堆積配置函式。|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|這個類別提供方法，以操作視窗。|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|這個類別提供方法來建立或子類別化視窗。|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|這個類別提供的方法標準化建立視窗物件時所使用的樣式。|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|這個類別提供的方法標準化建立視窗物件時所使用的樣式。|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|這個類別提供方法來註冊視窗類別資訊。|atlwin.h|
|[CWorkerThread 類別](../../atl/reference/cworkerthread-class.md)|這個類別會建立背景工作執行緒或使用現有工作區、 等候一或多個核心物件控制代碼，而且其中一個控點而收到信號時，執行指定的用戶端函式。|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|此類別代表介面`CreateInstance`方法。|atlbase.h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|此類別代表記憶體管理員介面。|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|這個介面會提供方法來指定裝載的控制項或容器的特性。|atlbase ATLIFace.h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|這個介面會實作補充環境裝載的控制項屬性。|atlbase ATLIFace.h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|這個介面會提供方法來操作控制項和其主機物件。|atlbase ATLIFace.h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|這個介面會提供管理授權的控制項和其主機物件的方法。|atlbase ATLIFace.h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|這個類別提供的集合類別所使用的方法。|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|這個類別會實作連接點容器來管理集合[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件。|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|這個類別會實作連接點。|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|這個類別提供方法來支援制式資料傳輸及管理連線。|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|這個類別提供的預設實作`IDispatch`雙重介面的一部分。|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|這個類別提供的實作`IDispatch`方法。|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|這個類別提供的實作`IDispatch`方法，而不需要從類型程式庫中取得類型資訊。|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|介面的 Microsoft HTML 剖析和轉譯引擎。|atlbase ATLIFace.h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|這個類別會定義根據 c + + 標準程式庫集合的列舉值介面。|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|這個類別提供的預設實作`IObjectSafety`介面，以允許用戶端會擷取和設定物件的安全性層級。|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|這個類別提供方法讓其站台與通訊的物件。|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|這個類別提供的預設實作`IOleControl`介面和實作`IUnknown`。|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|這個類別提供方法來協助就地控制項與其容器之間的通訊。|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|這個類別會實作`IUnknown`，並提供啟用無視窗控制項接收視窗訊息，以及參與拖放作業的方法。|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|這個類別會實作`IUnknown`和是透過此容器進行通訊與控制項的主要介面。|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|這個類別會實作`IUnknown`，並可讓用戶端來存取物件的屬性頁中的資訊。|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|這個類別會實作`IUnknown`，可讓用戶端提供的屬性包以儲存其屬性的物件。|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|這個類別會實作[IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage)介面。|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|這個類別會實作`IUnknown`，並提供的預設實作[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)介面。|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|這個類別會實作`IUnknown`而[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive)介面方法。|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|這個類別會公開[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)作為可連接物件上的連出介面的介面。|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|這個類別會實作`IUnknown`和繼承的預設實作[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)。|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|這個類別會實作`IUnknown`，並提供的預設實作[IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage)介面。|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|這個類別提供的預設實作[IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo)並[IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2)方法。|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|這個類別會結合成單一呼叫容器的控制項初始化。|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|這個類別會實作`IUnknown`，並提供的預設實作[IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject)介面。|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|這個類別提供的預設實作`IServiceProvider`介面。|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|這個類別會實作`IUnknown`，並提供的預設實作[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages)介面。|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|這個類別提供的預設實作`ISupportErrorInfo Interface`介面，並可以在只有單一介面產生物件錯誤時使用。|atlcom.h|
|[IThreadPoolConfig 介面](../../atl/reference/ithreadpoolconfig-interface.md)|這個介面會提供方法，以設定執行緒集區。|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|這個類別會實作`IUnknown`並提供的預設實作[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject)， [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2)，和[IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex)介面。|atlctl.h|
|[IWorkerThreadClient 介面](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` 是用戶端所實作的介面[CWorkerThread](../../atl/reference/cworkerthread-class.md)類別。|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|這個類別會提供包裝函式`CreateWindow`和`CreateWindowEx`。|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|這個引數的配接器類別可讓`RECT`指標或參考傳遞至函式實作方面的指標。|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|資源名稱 (LPCTSTRs)] 或 [資源識別碼 （所） 傳遞至函式，而不需要呼叫者識別碼轉換為使用 MAKEINTRESOURCE 巨集的字串，可讓這個引數的配接器類別。|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|這個類別會提供以 Windows 執行緒的建立函式。 如果執行緒不會使用 CRT 函式，請使用這個類別。|atlbase.h|

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[函式](../../atl/reference/atl-functions.md)<br/>
[全域變數](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
