---
title: ATL 類別和結構 |Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 2bf13700ada3284b8a32718d21971e89e30e5b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498041"
---
# <a name="atl-classes-and-structs"></a>ATL 類別與結構

Active Template Library （ATL）包含下列類別和結構。 若要依分類尋找特定類別，請參閱[ATL 類別的總覽](../../atl/atl-class-overview.md)。

|類別/結構|描述|標頭檔|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|包含用來轉譯成各種目標的資訊，例如印表機、中繼檔或 ActiveX 控制項。|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|在 ATL 中的視窗化程式碼中包含類別實例資料。|atlbase.h。h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|由任何使用 ATL 的專案所使用。|atlbase.h。h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|在 ATL 中由 COM 相關的程式碼使用。| atlbase.h。h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|包含用來描述分配介面上之方法或屬性的類型資訊。|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|包含每個 ATL 模組所使用的資料。|atlbase.h。h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|由 ATL 中的視窗化程式碼使用。|atlbase.h。h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|這個類別是由字串轉換宏 CA2TEX 和 CT2AEX，以及 typedef CA2A 所使用。|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|字串轉換宏 CA2CTEX 和 CT2CAEX 以及 typedef CA2CA 會使用這個類別。|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|這個類別是由字串轉換宏 CA2TEX、CA2CTEX、CT2WEX 和 CT2CWEX，以及 typedef CA2W 所使用。|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|此類別是存取權杖的包裝函式。|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|此類別是 ACL （存取控制清單）結構的包裝函式。|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|此範本用來包裝重新定義傳址 (address-of) 運算子的類別，以傳回物件位址以外的內容。|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|這個類別會實作為陣列物件。|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|這個類別會執行執行緒集區式的單元模型 COM 伺服器。|atlbase.h。h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|這個類別會提供方法來執行執行緒集區式的單元模型 COM 伺服器。|atlbase.h。h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|這個類別會在每個 ATL 專案中具現化。|atlcore。h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|這個類別會實行 COM 伺服器模組。|atlbase.h。h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|這個類別會提供對偵測介面的支援。|atlbase.h。h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|此類別代表 DLL 的模組。|atlbase.h。h|
|[CAtlException](../../atl/reference/catlexception-class.md)|這個類別會定義 ATL 例外狀況。|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|此類別代表應用程式的模組。|atlbase.h。h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|這個類別會提供 Windows 檔案處理 API 的精簡型包裝函式。|atlfile。h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|此類別代表記憶體對應檔，並將 cast 運算子加入至[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)的方法。|atlfile。h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|此類別代表記憶體對應檔。|atlfile。h|
|[CAtlList](../../atl/reference/catllist-class.md)|這個類別會提供建立和管理清單物件的方法。|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|這個類別會提供建立和管理地圖物件的方法。|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|這個類別提供數個 ATL 模組類別所使用的方法。|atlbase.h。h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|這個類別會實行 ATL 模組。|atlbase.h。h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|這個類別是視窗的 ATL 實作為，其放在 Shell 提供供豐富預覽的主機視窗上。|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|這個類別會執行服務。|atlbase.h。h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|這個類別會提供建立和使用暫存檔案的方法。|atlfile。h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|此類別提供核心交易管理員（KTM）函數的包裝函式。|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|這個類別會提供 ATL 視窗化元件的支援。|atlbase.h。h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|此類別代表智慧型指標物件。|atlbase.h。h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|這個類別會在建立智慧型指標的陣列時提供有用的方法。|atlbase.h。h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|這個類別會提供方法、靜態函式和 typedef，在建立智慧型指標的集合時很有用。|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|這個類別會在建立智慧型指標的清單時提供有用的方法。|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|此類別代表使用向量 new 和 delete 運算子的智慧型指標物件。|atlbase.h。h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|當使用向量 new 和 delete 運算子建立智慧型指標的集合時，這個類別會提供有用的方法、靜態函式和 typedef。|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|這個類別會執行裝載 ActiveX 控制項的對話方塊（強制回應或非強制回應）。|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|這個類別會提供方法來操作裝載 ActiveX 控制項的視窗。|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|這個類別會提供方法來操作裝載 ActiveX 控制項的視窗，也支援裝載授權的 ActiveX 控制項。|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|這個類別會實作 `IBindStatusCallback` 介面。|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|這個類別會為匯總的物件實作為[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|這個類別會提供使用 COM 記憶體常式來管理記憶體的方法。|atlbase.h。h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|此類別提供線上程集區 EXE 模組中管理單元的支援。|atlbase.h。h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|這個類別會提供方法來取得和釋放重要區段物件的擁有權。|atlcore。h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|從 atl 7.0，已`CComAutoThreadModule`過時：如需詳細資訊，請參閱[atl 模組](../../atl/atl-module-classes.md)。|atlbase.h。h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|這個類別是 Bstr 的包裝函式。|atlbase.h。h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|這個類別會針對卸載介面來實行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|這個類別會實[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面。|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|這個類別會實[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)介面。|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|這個類別會實[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)介面，並允許在多個單元中建立物件。|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|這個類別衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，並使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建立單一物件。|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|這個類別會提供方法來建立類別的實例，並取得其屬性。|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|這個類別會提供執行複合控制項所需的方法。|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|這個類別會藉由委派給擁有者物件的`IUnknown`來實作為 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|這個類別會提供建立和管理 ATL 控制項的方法。|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|這個類別會提供建立和管理 ATL 控制項的方法。|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|這個類別會提供方法來取得和釋放重要區段物件的擁有權。|atlcore。h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|這個類別會提供鎖定和解除鎖定重要區段物件的方法。|atlbase.h。h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|這個類別具有用來建立和管理貨幣物件的方法和運算子。|atlcur.h。h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|這個類別會儲存指標的`IUnknown`陣列。|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|這個類別會定義以陣列為基礎的 COM 列舉值物件。|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|這個類別會提供 COM 列舉值介面的實值，其中要列舉的專案會儲存在陣列中。|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|此類別會定義以C++標準程式庫集合為基礎的 COM 列舉值物件。|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|這個類別提供的方法與[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)相同，但不提供重要區段。|atlcore。h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|這個類別會提供處理介面指標和全域介面表（GIT）的方法。|atlbase.h。h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|這個類別會使用 COM 記憶體配置函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|用於管理堆積指標的智慧型指標類別。|atlbase.h。h|
|[CComModule](../../atl/reference/ccommodule-class.md)|從 atl 7.0，已`CComModule`過時：如需詳細資訊，請參閱[atl 模組](../../atl/atl-module-classes.md)。|atlbase.h。h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|這個類別會提供安全線程的方法，以遞增和遞減變數的值。|atlbase.h。h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|這個類別會提供安全線程的方法，以遞增和遞減變數的值，而不需要重要區段鎖定或解除鎖定功能。|atlbase.h。h|
|[CComObject](../../atl/reference/ccomobject-class.md)|這個類別`IUnknown`會針對非匯總物件進行。|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|此類別會管理包含您`Base`的物件之模組上的參考計數。|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|這個類別`IUnknown`會針對非匯總物件進行實作為，但不會遞增此函式中的模組鎖定計數。|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|此[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的 typedef 是在伺服器的預設執行緒模型上範本化。|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|這個類別會提供方法來處理非匯總和匯總物件的物件參考計數管理。|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|這個類別會建立一個暫存的 COM 物件，並為它提供的`IUnknown`框架執行。|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|這個類別`IUnknown`會針對匯總或非匯總物件來執行。|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|用於管理 COM 介面指標的智慧型指標類別。|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|這個類別會使用以 COM 為基礎的記憶體常式來提供智慧型指標類別的基礎。|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|用於管理 COM 介面指標的智慧型指標類別。|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|這個類別會在建立 COM 介面指標的集合時，提供有用的方法、靜態函式和 typedef。|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|這個類別是`SAFEARRAY Data Type`結構的包裝函式。|atlsafe.h。h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|這個類別是`SAFEARRAYBOUND`結構的包裝函式。|atlsafe.h。h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|這個類別會管理類別[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的執行緒選取專案。|atlbase.h。h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|這個類別會提供方法來遞增和遞減變數的值。|atlbase.h。h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|這個類別會執行一個卸載介面。|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|這個類別會`IUnknown`儲存指標，而且是設計用來當做[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)樣板類別的參數。|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|這個類別會包裝 VARIANT 型別，並提供成員來指出儲存的資料型別。|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|這個類別會執行包含在另一個物件中的視窗。|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|這個類別會提供使用 CRT 記憶體常式來管理記憶體的方法。|atlcore。h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|這個類別會使用 CRT 堆積函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|這個類別是 DACL （任意存取控制清單）結構的包裝函式。|atlsecurity.h|
|[CDebugReportHook 類別](../../atl/reference/cdebugreporthook-class.md)|使用這個類別，即可將 debug 報表傳送到具名管道。|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|這個類別提供兩個靜態函式，用來轉換大寫和小寫之間的字元。|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|這個類別會提供預設的元素比較函式。|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|這個類別會提供集合類別的預設方法和函式。|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|這個類別會提供用來計算雜湊值的靜態函式。|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|這個類別提供建立模式或非強制回應對話方塊的方法。|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|這個類別會提供支援訊息對應之動態連結的方法。|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|集合類別會使用這個類別來提供用於移動、複製、比較和雜湊作業的方法和函數。|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|這個類別會提供集合類別的預設複製和移動方法。|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|這個類別會提供方法來通知容器有關控制項屬性變更的接收。|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|這個類別會使用 Win32 全域堆積函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|這個類別會提供建立和使用 handle 物件的方法。|atlbase.h。h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|用於管理堆積指標的智慧型指標類別。|atlcore。h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|這個類別會形成數個智慧堆積指標類別的基礎。|atlcore。h|
|[CHeapPtrElementTraits 類別](../../atl/reference/cheapptrelementtraits-class.md)|在建立堆積指標的集合時，這個類別提供有用的方法、靜態函數和 typedef。|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|這個類別會在建立堆積指標清單時提供有用的方法。|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供增強的點陣圖支援，包括以 JPEG、GIF、BMP 和可移植網狀圖形（PNG）格式載入和儲存影像的能力。|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|這個類別會在建立 COM 介面指標的陣列時提供有用的方法。|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|這個類別會在建立 COM 介面指標的清單時，提供有用的方法。|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|這個類別會使用 Win32 本機堆積函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|這個類別允許另一個物件存取物件的訊息對應。|atlwin.h|
|[CNonStatelessWorker 類別](../../atl/reference/cnonstatelessworker-class.md)|接收來自執行緒集區的要求，並將它們傳遞至在每個要求上建立和終結的背景工作物件。|atlutil.h|
|[CNoWorkerThread 類別](../../atl/reference/cnoworkerthread-class.md)|如果您想要停用動態快`MonitorClass`取維護，請使用這個類別做為範本參數快取類別的引數。|atlutil.h|
|[CPathT 類別](../../atl/reference/cpatht-class.md)|此類別代表路徑。|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|這個類別會針對由基本資料類型組成的集合類別，提供預設的方法和函式。|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|此類別代表私用物件安全描述項物件。|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|此類別代表使用紅色-黑色二進位樹狀結構的對應結構。|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|此類別代表一個對應結構，允許每個索引鍵與一個以上的值建立關聯，並使用紅色-黑色二進位樹狀目錄。|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|此類別提供建立和使用紅色-黑色樹狀結構的方法。|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|這個類別會提供方法來作業系統註冊表中的專案。|atlbase.h。h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|這個類別會提供 CRT 執行緒的建立函式。 如果執行緒將使用 CRT 函式，請使用這個類別。|atlbase.h。h|
|[CSacl](../../atl/reference/csacl-class.md)|這個類別是 SACL （系統存取控制清單）結構的包裝函式。|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|這個類別是`SECURITY_ATTRIBUTES`結構的精簡包裝函式。|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|這個類別是`SECURITY_DESCRIPTOR`結構的包裝函式。|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|這個類別是`SID` （安全識別碼）結構的包裝函式。|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|這個類別提供管理簡單陣列的方法。|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|這個類別是[CSimpleArray](../../atl/reference/csimplearray-class.md)類別的 helper。|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|這個類別是[CSimpleArray](../../atl/reference/csimplearray-class.md)類別的 helper。|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|這個類別會實行基本強制回應對話方塊。|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|這個類別會提供簡單對應陣列的支援。|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|這個類別是[CSimpleMap](../../atl/reference/csimplemap-class.md)類別的 helper。|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|這個類別是[CSimpleMap](../../atl/reference/csimplemap-class.md)類別的 helper。|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|這個類別會提供用來執行嵌入式管理單元節點物件的方法。|atlsnap。h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|這個類別會提供用來執行嵌入式管理單元屬性頁物件的方法。|atlsnap。h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|這個類別會提供支援內建屬性值的方法。|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|這個類別會提供用來儲存`CString`物件之集合類別所使用的靜態函式。|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|這個類別會提供與集合類別物件中所儲存之字串相關的靜態函式。 它類似于[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但會執行不區分大小寫的比較。|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|這個類別會提供與集合類別物件中所儲存之字串相關的靜態函式。 字串物件會以參考的形式處理。|atlcoll.h|
|[CThreadPool 類別](../../atl/reference/cthreadpool-class.md)|這個類別會提供可處理工作專案佇列的背景工作執行緒集區。|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|這個類別是`TOKEN_GROUPS`結構的包裝函式。|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|這個類別是`TOKEN_PRIVILEGES`結構的包裝函式。|atlsecurity.h|
|[CUrl 類別](../../atl/reference/curl-class.md)|此類別代表 URL。 除了剖析現有的 URL 字串或從頭開始建立字串之外，它還可讓您管理 URL 的每個專案，而不受其他元素影響。|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|這個類別是由字串轉換宏 CT2AEX、CW2TEX、CW2CTEX 和 CT2CAEX，以及 typedef CW2A 所使用。|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|這個類別是由字串轉換宏 CW2CTEX 和 CT2CWEX，以及 typedef CW2CW 所使用。|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|這個類別是由字串轉換宏 CW2TEX 和 CT2WEX，以及 typedef CW2W 所使用。|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|這個類別會使用 Win32 堆積配置函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|這個類別提供操作視窗的方法。|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|這個類別會提供建立或子類別化視窗的方法。|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|這個類別會提供一個方法，以標準化建立視窗物件時所使用的樣式。|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|這個類別會提供一個方法，以標準化建立視窗物件時所使用的樣式。|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|這個類別會提供註冊視窗類別之資訊的方法。|atlwin.h|
|[CWorkerThread 類別](../../atl/reference/cworkerthread-class.md)|這個類別會建立背景工作執行緒，或使用現有的一個或多個核心物件控制碼，並在其中一個控制碼收到信號時，執行指定的用戶端函式。|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|此類別代表`CreateInstance`方法的介面。|atlbase.h。h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|此類別代表記憶體管理員的介面。|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|這個介面會提供方法來指定裝載控制項或容器的特性。|atlbase.h .h，ATLIFace。h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|這個介面會實作為裝載控制項的補充環境屬性。|atlbase.h .h，ATLIFace。h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|這個介面提供操作控制項及其主機物件的方法。|atlbase.h .h，ATLIFace。h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|這個介面提供操作授權控制項及其主機物件的方法。|atlbase.h .h，ATLIFace。h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|這個類別會提供集合類別所使用的方法。|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|此類別會執行連接點容器，以管理[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件的集合。|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|這個類別會執行連接點。|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|這個類別提供支援制式資料傳輸和管理連接的方法。|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|這個類別會為雙重介面的`IDispatch`部分提供預設的執行。|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|這個類別會提供`IDispatch`方法的執行。|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|這個類別會提供`IDispatch`方法的執行，而不需要從類型程式庫取得類型資訊。|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Microsoft HTML 剖析和轉譯引擎的介面。|atlbase.h .h，ATLIFace。h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|這個類別會定義以C++標準程式庫集合為基礎的列舉值介面。|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|這個類別會提供`IObjectSafety`介面的預設執行，以允許用戶端抓取和設定物件的安全性層級。|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|這個類別提供的方法可讓物件與網站進行通訊。|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|這個類別會提供`IOleControl`介面的預設實作為`IUnknown`，並加以執行。|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|這個類別會提供方法來協助就地控制項與其容器之間的通訊。|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|這個類別`IUnknown`會執行並提供方法，以啟用無視窗控制項來接收視窗訊息，以及參與拖放作業。|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|這個類別`IUnknown`會執行，而是容器用來與控制項通訊的主要介面。|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|這個類別`IUnknown`會執行並允許用戶端存取物件屬性頁中的資訊。|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|這個類別`IUnknown`會執行並允許物件將其屬性儲存至用戶端提供的屬性包。|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|這個類別會實[IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage)介面。|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|這個類別`IUnknown`會執行並提供[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面的預設實值。|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|這個類別`IUnknown`會執行和[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)介面方法。|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|這個類別會將[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面公開為可連線物件上的輸出介面。|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|這個類別`IUnknown`會執行並繼承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的預設實值。|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|這個類別`IUnknown`會執行並提供[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)介面的預設實值。|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|這個類別會提供[IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)和[iprovideclassinfo2.getguid](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)方法的預設執行。|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|這個類別會將容器的控制項初始化結合成單一呼叫。|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|這個類別`IUnknown`會執行並提供[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)介面的預設實值。|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|這個類別會提供`IServiceProvider`介面的預設執行。|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|這個類別`IUnknown`會執行並提供[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)介面的預設實值。|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|這個類別會提供`ISupportErrorInfo Interface`介面的預設執行，而且可以在只有單一介面產生物件錯誤時使用。|atlcom.h|
|[IThreadPoolConfig 介面](../../atl/reference/ithreadpoolconfig-interface.md)|這個介面提供設定執行緒集區的方法。|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|這個`IUnknown`類別會執行並提供[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)介面的預設執行。|atlctl.h|
|[IWorkerThreadClient 介面](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient`是由[CWorkerThread](../../atl/reference/cworkerthread-class.md)類別的用戶端所執行的介面。|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|這個類別會提供和`CreateWindow` `CreateWindowEx`的包裝函式。|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|這個引數介面卡類別`RECT`允許將指標或參考傳遞至以指標來實作為實作用的函式。|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|這個引數介面卡類別允許將資源名稱（LPCTSTRs）或資源識別碼（UINTs）傳遞至函式，而不需要呼叫者使用 MAKEINTRESOURCE 宏將識別碼轉換成字串。|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|這個類別會提供 Windows 執行緒的建立函式。 如果執行緒不會使用 CRT 函式，請使用這個類別。|atlbase.h。h|

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[函式](../../atl/reference/atl-functions.md)<br/>
[全域變數](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
