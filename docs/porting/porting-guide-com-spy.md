---
title: 移植指南：COM Spy
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: c21049a2faa8bb34ecd1ba75a5beda1db119f0fc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230281"
---
# <a name="porting-guide-com-spy"></a>移植指南：COM Spy

本主題是系列文章中的第二個主題，示範將舊版 Visual Studio C++ 專案升級至最新版 Visual Studio 的程序。 本主題中的範例程式碼最後是使用 Visual Studio 2005 所編譯。

## <a name="comspy"></a>COMSpy

COMSpy 是用來監視和記錄電腦上之 Serviced 元件活動的程式。 Serviced 元件是指在系統上執行，並且可供相同網路上的電腦使用的 COM+ 元件。 這些元件是由 Windows 控制台中的 [元件服務] 功能所管理。

### <a name="step-1-converting-the-project-file"></a>步驟 1： 轉換專案檔

專案檔的轉換很容易，而且會產生移轉報告。 報告中的幾個項目提供可能需要處理之問題的相關資訊。 以下是回報的一個問題 (請注意，在本主題中，有時會縮短錯誤訊息以利閱讀，例如移除完整路徑)：

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

升級專案的其中一個常見問題，就是 [專案屬性] 對話方塊中的 [**連結器 OutputFile** ] 設定可能需要經過檢查。 對於 Visual Studio 2010 之前的專案而言，當 OutputFile 設定為非標準值時，就會造成自動轉換精靈的問題。 在這種情況下，輸出檔案的路徑會設定為非標準資料夾 XP32_DEBUG。 為了深入了解這個錯誤，我們查閱了與 Visual Studio 2010 專案升級相關的[部落格文章](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/)，這個升級涉及一項重大的變更，那就是從 vcbuild 變更為 msbuild。 根據這項資訊，當您建立新專案時，**輸出檔案**設定的預設值為 `$(OutDir)$(TargetName)$(TargetExt)`，但由於轉換的專案無法確認一切正確，因此不會在轉換期間進行這項設定。 不過，讓我們試放在 OutputFile 中，看看是否可行。  結果可行，因此我們可以繼續進行。 如果沒有特別原因需要使用非標準輸出資料夾，建議使用標準位置。 在本例中，我們選擇在移植和升級過程中保留非標準輸出位置；`$(OutDir)` 在**偵錯**組態中會解析成 XP32_DEBUG 資料夾，在**發行**組態中會解析成 ReleaseU 資料夾。

### <a name="step-2-getting-it-to-build"></a>步驟 2： 建置專案

建置已移植的專案時，會發生一些錯誤和警告。

`ComSpyCtl` 由於下列編譯器錯誤而不會進行編譯：

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

該錯誤會在 atlcom.h 中參考 `IPersistStreamInitImpl` 類別的 `Save` 方法。

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

問題在於舊版編譯器接受的轉換不再有效。 為了符合 C++ 標準，不再允許使用之前所允許的一些程式碼。 在這種情況下，將非 const 指標傳遞給必須有 const 指標的函式並不安全。  解決方法是在 `CComSpy` 類別找到 `IPersistStreamInit_Save` 的宣告，然後將 const 修飾詞新增到第三個參數。

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

並對 `IPersistStreamInit_Load` 進行類似的變更。

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

下一個錯誤與註冊相關。

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

我們不再需要這個建置後註冊命令。 相反地，我們只會移除自訂群組建命令，並在**連結器**設定中指定來註冊輸出。

### <a name="dealing-with-warnings"></a>處理警告

這個專案會產生下列連結器警告。

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

`/SAFESEH` 編譯器選項不適用於偵錯模式，`/EDITANDCONTINUE` 才適用，因此修正方法是只對**偵錯**組態停用 `/SAFESEH`。 若要在屬性對話方塊中執行這項作業，請開啟產生這個錯誤的專案屬性對話方塊，先將**組態**設定為**偵錯** (實際上是**對 Unicode 偵錯**)，然後在 [連結器進階]**** 區段中，將 [映像有安全例外狀況處理常式]**** 重設為 [否]**** (`/SAFESEH:NO`)。

編譯器會警告我們，`PROP_ENTRY_EX` 即將淘汰。 這並不安全，建議改用 `PROP_ENTRY_TYPE_EX`。

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

問題在於宣告 `i` 為 `UINT` 並宣告 `lCount` 為 **`long`** ，因此已簽署/不帶正負號的不相符。 將的類型變更為是不方便的 `lCount` `UINT` ，因為它會從取得其值 `IMtsEventInfo::get_Count` ，其使用類型 **`long`** ，而不是在使用者程式碼中。 因此我們在程式碼中加入一個轉換。 C 樣式轉換會針對數值轉換（例如這個）執行，但 **`static_cast`** 是建議的樣式。

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

當變數宣告所在的函式具有相同名稱的參數，而導致可能使人混淆的程式碼時，就會發生這些警告。 藉由變更區域變數的名稱，已修正這個問題。

### <a name="step-3-testing-and-debugging"></a>步驟 3： 測試和偵錯

測試應用程式時，請先執行各種功能表和命令，然後再關閉應用程式。 唯一需要注意的問題是關閉應用程式時的偵錯判斷提示。 這個問題出現在應用程式的主要 COM 元件：`CWindowImpl` (`CSpyCon` 物件的基底類別) 的解構函式。 atlwin.h 中的下列程式碼發生判斷提示失敗。

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

`hWnd` 通常在 `WindowProc` 函式中會設定為零，但這卻沒有發生，因為關閉視窗的 Windows 訊息 (WM_SYSCOMMAND) 呼叫了自訂處理常式，而不是預設的 `WindowProc`。 而自訂處理常式並未將 `hWnd` 設定為零。 請查看 MFC `CWnd` 類別中的類似程式碼，該程式碼顯示在終結視窗時，會呼叫 `OnNcDestroy`；至於在 MFC，文件則建議在覆寫 `CWnd::OnNcDestroy` 時，應該呼叫基底 `NcDestroy`，以確保進行正確的清除作業，包括將視窗控制代碼與視窗分隔，也就是將 `hWnd` 設定為零。 範例的原始版本中可能也觸發了這個判斷提示，因為舊版 atlwin.h 中已有相同的判斷提示程式碼。

為了測試應用程式的功能，我們使用 ATL 專案範本建立了一個**服務元件**，並在 atl 專案嚮導中加入宣告 com + 支援。 如果您之前未使用過服務的元件，就不會很容易建立一個，並在系統或網路上註冊並取得，供其他應用程式使用。 COM Spy 應用程式的設計是為了當做診斷輔助工具，來監視 Serviced 元件的活動。

然後，我們新增類別、選擇 ATL 物件，並將物件名稱指定為 `Dog`。 再於 dog.h 和 dog.cpp 中加入實作。

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

接下來，我們已建立並註冊它（您必須以系統管理員身分執行 Visual Studio），並使用 Windows 控制台中的 [**服務元件**] 應用程式加以啟用。 我們建立 C# Windows Form 專案，從工具箱拖曳一個按鈕到表單，然後按兩下以開啟 Click 事件處理常式。 我們新增下列程式碼來將 `Dog` 元件具現化。

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

其執行沒有問題，並因為 COM Spy 已啟動並執行，而且設定為監視 `Dog` 元件，因此會出現許多顯示活動的資料。

## <a name="see-also"></a>另請參閱

[移植和升級：範例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[下一個範例：Spy++](../porting/porting-guide-spy-increment.md)<br/>
[上一個範例︰MFC Scribble](../porting/porting-guide-mfc-scribble.md)
