---
title: "如何：使用 Interop 組件匯入設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE 設定, 使用 Interop 組件匯入"
  - "IDE, 使用 Interop 組件匯入設定"
  - "使用者設定 [Visual Studio SDK], 使用 Interop 組件匯入"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# 如何：使用 Interop 組件匯入設定
VSPackage 可能會從 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 匯入設定。 IDE 使用 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面實作，來判斷如何擷取 VSPackage 的組態。  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) 提供一組 Managed 類別來加速建立 Visual Studio 擴充功能。 若要使用 MPF 來執行這項工作，請參閱[匯入設定](../misc/importing-settings.md)。  
  
### 在 VSPackage 上實作設定匯入  
  
1.  實作 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 設定機制的基本支援。  
  
    -   透過定義一個或多個自訂設定點，以將 VSPackage 註冊為支援設定機制。  
  
         如需詳細資訊，請參閱[使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)。  
  
    -   宣告 VSPackage 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面，例如：  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   請確定 VSPackage 的 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 方法實作在使用 `IID_IVsUserSettings` 呼叫時提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面。 例如:  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  擷取設定資訊。  
  
     若要支援擷取設定資訊，VSPackage 必須實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法。  
  
     若要讀取資料，VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面實作必須使用 IDE 所傳入的前兩個引數：該自訂設定點分類的 GUID 以及 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 介面。  
  
    1.  VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法實作必須檢查傳入的分類 GUID，並選擇正確的機制來擷取狀態。  
  
         在下面範例中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法會呼叫不同的實作來擷取命令列狀態，而不是擷取索引鍵繫結狀態。  
  
    2.  VSPackage 必須使用提供的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 介面，將資料擷取至設定檔。  
  
        > [!NOTE]
        >  如果設定資訊變更為 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本的函式，則 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法實作必須在讀取資料之前，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> 方法來檢查 IDE 版本。  
  
         介面會提供方法來讀取設定檔中的不同資料類型。  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     設定檔支援隨機資料存取，因此讀取和寫入設定作業的順序不重要。  
  
     這在下面範例中實作的匯出和匯入命令列狀態 \(`ExportSettings_CommandBa`r 和 `ImportSettings_CommandBar`\) 中予以說明。  
  
3.  驗證擷取的資料。  
  
     設定資訊包含在可手動編輯的 XML 檔案中。  
  
> [!IMPORTANT]
>  設定資訊在磁碟上可能損毀、可能包含版本特定設定，以及可能用作惡意攻擊的工具。 應該驗證 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 方法所傳回之每個資料項目的有效性。  
  
-   若要驗證用來產生所擷取設定之 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本的支援，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> 方法來擷取版本。  
  
-   若要讓 IDE 通知使用者未驗證匯入的資料項目，則 VSPackage 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A> 方法。  
  
1.  套用設定資訊。  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法的實作必須遵守 IDE 傳遞給它之第三個引數的值。 支援的值為 <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags> 列舉的成員。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>。  
  
         在下面範例中，匯入命令列設定的實作 \(`ImportSettings_Commandbar`\) 使用這個引數的值判斷是要套用設定來覆寫現有值，還是額外更新這些值。  
  
    2.  套用匯入的設定時，您必須實作直接寫入式快取方法。  
  
         將設定套用至 IDE 時，必須同時更新登錄或檔案系統中的狀態資訊。 這可確保組態一致性，並支援多執行個體 IDE 案例。  
  
2.  警示 IDE 如何處理設定匯入。  
  
     使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法的已傳回 `pfRestartRequired` 引數，來建議 IDE 是否需要重新啟動來套用匯入的設定。  
  
     如果 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法實作傳回 `true`，則系統會提示使用者重新啟動 IDE。  
  
## 範例  
 這個範例示範如何匯入和匯出設定資料。  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## 請參閱  
 [如何：使用 Interop 組件匯出設定](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)   
 [擴充使用者設定和選項](../Topic/Extending%20User%20Settings%20and%20Options.md)   
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)