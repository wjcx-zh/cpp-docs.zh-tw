---
title: "移植指南：COM Spy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5e30d0664716df0f4cdf7d394d9c9a5fd7e8c798
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="porting-guide-com-spy"></a>移植指南：COM Spy
本主題是系列文章中的第二個主題，示範將舊版 Visual C++ 專案升級至最新版 Visual Studio 的程序。 本主題中的範例程式碼最後是使用 Visual Studio 2005 所編譯。  
  
## <a name="comspy"></a>COMSpy  
 COMSpy 是用來監視和記錄電腦上之 Serviced 元件活動的程式。 Serviced 元件是指在系統上執行，並且可供相同網路上的電腦使用的 COM+ 元件。 這些元件是由 Windows 控制台中的 [元件服務] 功能所管理。  
  
### <a name="step-1-converting-the-project-file"></a>步驟 1： 轉換專案檔。  
 專案檔的轉換很容易，而且會產生移轉報告。 報告中的幾個項目提供可能需要處理之問題的相關資訊。 以下是回報的一個問題 (請注意，在本主題中，有時會縮短錯誤訊息以利閱讀，例如移除完整路徑)：  
  
```Output  
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).  
```  
  
 升級專案的其中一個常見問題是，專案屬性對話方塊中的連結器 OutputFile 設定可能需要檢閱。 對於 Visual Studio 2010 之前的專案而言，當 OutputFile 設定為非標準值時，就會造成自動轉換精靈的問題。 在這種情況下，輸出檔的路徑會設定為非標準資料夾 XP32_DEBUG。 為了深入了解這個錯誤，我們查閱了與 Visual C++ 2010 專案升級相關的[部落格文章](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)，這個升級涉及一項重大的變更，那就是從 vcbuild 變更為 msbuild。 根據這項資訊，當您建立新專案時，[輸出檔案] 設定的預設值為 $(OutDir)$(TargetName)$(TargetExt)，但由於轉換的專案無法確認一切正確，因此不會在轉換期間進行這項設定。  不過，讓我們試放在 OutputFile 中，看看是否可行。  結果可行，因此我們可以繼續進行。 如果沒有特別原因需要使用非標準輸出資料夾，建議使用標準位置。 在本例中，我們選擇在移植和升級程序期間保留非標準輸出位置；$(OutDir) 在偵錯組態中會解析成 XP32_DEBUG 資料夾，在發行組態中會解析成 ReleaseU 資料夾。  
  
### <a name="step-2-getting-it-to-build"></a>步驟 2： 建置專案  
 建置已移植的專案時，會發生一些錯誤和警告。  
  
 ComSpyCtl 由於下列編譯器錯誤而不會進行編譯：  
  
```Output  
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled  
```  
  
 這個錯誤參考 atlcom.h 中 IPersistStreamInitImpl 類別上的 Save 方法。  
  
```cpp  
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)  
{  
     T* pT = static_cast<T*>(this);  
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));  
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());  
}  
```  
  
 問題在於舊版編譯器接受的轉換不再有效。 為了符合 C++ 標準，不再允許使用之前所允許的一些程式碼。 在這種情況下，將非 const 指標傳遞給必須有 const 指標的函式並不安全。  解決方法是在 CComSpy 類別上找到 IPersistStreamInit_Save 的宣告，然後將 const 修飾詞加入第三個參數。  
  
```cpp  
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)  
  
```  
  
 IPersistStreamInit_Load 會有類似的變更。  
  
```cpp  
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);  
```  
  
 下一個錯誤與註冊相關。  
  
```Output  
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.  
```  
  
 我們不再需要這個建置後註冊命令。 相反地，我們會直接移除自訂建置命令，並在連結器設定中指定要註冊輸出。  
  
### <a name="dealing-with-warnings"></a>處理警告  
 這個專案會產生下列連結器警告。  
  
```Output  
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification  
```  
  
 /SAFESEH 編譯器選項不適用於偵錯模式，/EDITANDCONTINUE 才適用，因此修正方法為只針對偵錯組態停用 /SAFESEH。 若要在屬性對話方塊中執行這項作業，請開啟產生這個錯誤之專案的屬性對話方塊，先將組態設定為偵錯 (實際上是偵錯 Unicode)，然後在連結器 [進階] 區段中，將 [映像有安全例外狀況處理常式] 重設為 [否 (/SAFESEH:NO)]。  
  
 編譯器警告我們 PROP_ENTRY_EX 已被取代。 這並不安全，建議改用 PROP_ENTRY_TYPE_EX。  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 我們據此在 ccomspy.h 中變更程式碼，並視需要加入 COM 類型。  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)  
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 剩下最後幾個警告是由於更嚴格的編譯器一致性檢查所造成：  
  
```Output  
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'  
```  
  
 警告 C4018 來自下列程式碼：  
  
```cpp  
for (i=0;i<lCount;i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 問題在於 i 宣告為 UINT，而 lCount 宣告為 long，因此 signed/unsigned 不相符。 無法將 lCount 的類型變更為 UINT，因為取得其值的來源 IMtsEventInfo::get_Count 使用 long 類型，而且不在使用者程式碼中。 因此我們在程式碼中加入一個轉換。 C-Style 轉換可執行類似本例的數值轉換，但建議使用 static_cast 樣式。  
  
```cpp  
for (i=0;i<static_cast<UINT>(lCount);i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 當變數宣告所在的函式具有相同名稱的參數，而導致可能使人混淆的程式碼時，就會發生這些警告。 藉由變更區域變數的名稱，已修正這個問題。  
  
### <a name="step-3-testing-and-debugging"></a>步驟 3： 測試和偵錯  
 測試應用程式時，請先執行各種功能表和命令，然後再關閉應用程式。 唯一需要注意的問題是關閉應用程式時的偵錯判斷提示。 這個問題出現在應用程式主要 COM 元件 CSpyCon 物件之基底類別 CWindowImpl 的解構函式中。 atlwin.h 中的下列程式碼發生判斷提示失敗。  
  
```cpp  
virtual ~CWindowImplRoot()  
{  
     #ifdef _DEBUG  
     if(m_hWnd != NULL)// should be cleared in WindowProc  
     {  
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));  
          ATLASSERT(FALSE);  
     }  
     #endif //_DEBUG  
}  
```  
  
 hWnd 通常在 WindowProc 函式中會設定為零，但卻未這麼做，因為關閉視窗的 Windows 訊息 (WM_SYSCOMMAND) 呼叫了自訂處理常式，而不是預設的 WindowProc。 而自訂處理常式並未將 hWnd 設定為零。 請查看 MFC CWnd 類別中的類似程式碼，該程式碼顯示當視窗正在被終結時，會呼叫 OnNcDestroy；而 MFC 文件則建議，當覆寫 CWnd::OnNcDestroy 時，應該呼叫基底 NcDestroy，以確保進行正確的清除作業，包括將視窗控制代碼與視窗分隔 (也就是將 hWnd 設定為零)。 範例的原始版本中可能也觸發了這個判斷提示，因為舊版 atlwin.h 中已有相同的判斷提示程式碼。  
  
 為了測試應用程式的功能，我們使用 ATL 專案範本建立 Serviced 元件，並在 ATL 專案精靈中選擇加入 COM+ 支援。 如果您之前沒有使用過 Serviced 元件，建立並註冊一個元件，以供系統或網路上的其他應用程式使用，其實並不困難。 COM Spy 應用程式的設計是為了當做診斷輔助工具，來監視 Serviced 元件的活動。  
  
 然後，我們加入一個類別、選擇 ATL 物件，並將物件名稱指定為 Dog， 再於 dog.h 和 dog.cpp 中加入實作。  
  
```cpp  
STDMETHODIMP CDog::Wag(LONG* lDuration)  
{  
    // TODO: Add your implementation code here  
    *lDuration = 100l;  
    return S_OK;  
}  
```  
  
 接著，我們建立及註冊元件 (您必須以系統管理員身分執行 Visual Studio)，然後使用 Windows 控制台中的 Serviced 元件應用程式加以啟動。 我們建立 C# Windows Form 專案，從工具箱拖曳一個按鈕到表單，然後按兩下以開啟 Click 事件處理常式。 我們加入下列程式碼來具現化 Dog 元件。  
  
```cpp  
private void button1_Click(object sender, EventArgs e)  
{  
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();  
    dog1.Wag();  
}  
```  
  
 這項執行沒有問題，COM Spy 已啟動並正在執行，而且設定為監視 Dog 元件，因此會出現許多顯示活動的資料。  
  
## <a name="see-also"></a>另請參閱  
 [移植和升級：範例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [下一個範例：Spy++](../porting/porting-guide-spy-increment.md)   
 [上一個範例︰MFC Scribble](../porting/porting-guide-mfc-scribble.md)