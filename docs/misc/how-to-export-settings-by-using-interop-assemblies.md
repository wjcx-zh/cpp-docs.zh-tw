---
title: "如何：使用 Interop 組件匯出設定 | Microsoft Docs"
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
  - "IDE 設定, 使用 Interop 組件匯出"
  - "使用者設定 [Visual Studio SDK], 使用 Interop 組件匯出"
  - "IDE, 使用 Iinterop 組件匯出設定"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 如何：使用 Interop 組件匯出設定
VSPackage 可能會從 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 匯出設定。 IDE 使用 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面實作。 如果封裝也提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 介面，則會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 介面來判斷要如何儲存 VSPackage 的組態。  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) 提供一組 Managed 類別來加速建立 Visual Studio 擴充功能。 若要使用 MPF 來執行這項工作，請參閱[匯出設定](../misc/exporting-settings.md)。  
  
### 在 VSPackage 上實作設定匯出  
  
1.  實作 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 設定機制的基本支援。  
  
    -   透過定義一個或多個自訂設定點，以將 VSPackage 註冊為支援設定機制。  
  
         如需詳細資訊，請參閱[使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)。  
  
    -   宣告 VSPackage 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>。 如果需要，VSPackage 也可以實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 介面。 例如:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   請確定 VSPackage 的 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 方法實作在使用 `IID_IVsUserSettings` 呼叫時提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面。  
  
         選擇性，`QueryInterface` 可以在使用 `IID_IVsUserSettingsQuery` 介面呼叫時提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 介面。  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  選擇性，提醒 IDE 需要匯出特定設定。  
  
     VSPackage 可以選擇有條件地儲存自訂設定點狀態所定義的設定。 例如，只有在使用者明確地表示要儲存設定時才儲存。  
  
     在這種情形下，必須實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 介面。  
  
     如果 VSPackage 未實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>，則會在設定匯出期間儲存其所有狀態資訊。  
  
     VSPackage 可以支援多個自訂設定點 \(設定類別\)。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A> 方法的實作必須檢查所提供自訂設定點的 GUID 或設定類別引數，來判斷是否必須儲存一組特定設定。  
  
     在下面範例中，VSPackage 一律會要求儲存其命令列狀態，但在已設定旗標時，則只會要求儲存其索引鍵繫結狀態。  
  
3.  請將設定資料寫入檔案。  
  
     若要支援匯出設定，VSPackage 必須一律實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 方法。  
  
     這項實作必須處理 IDE 所傳遞的引數、該自訂設定點類別的 GUID 以及 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 介面。  
  
    1.  VSPackage 可以支援多個自訂設定點 \(設定類別\)。 在下面範例中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 方法會呼叫不同的實作來保存命令列狀態，而不是保存索引鍵繫結狀態。  
  
    2.  VSPackage 必須使用提供的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 介面，將資料儲存至設定檔案。  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         提供給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 介面的 `pszSettingName` 引數值必須唯一識別設定類別內所儲存的每個資料項目。  
  
        > [!NOTE]
        >  名稱在自訂設定點內必須是唯一的，因為 IDE 使用其 GUID 以及 `pszSettingName` 的值來識別每個儲存的設定。 如果使用相同的 `pszSettingName` 值來呼叫多個 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 方法，則會覆寫設定檔案中的原始值。  
  
         設定檔案支援隨機資料存取。 因此，讀取和寫入設定作業的順序不重要。  
  
         這在下面範例中的匯出和匯入命令列狀態 \(`ExportSettings_CommandBa`r 和 `ImportSettings_CommandBar`\) 實作中予以說明。  
  
         如果實作可以將資料對應至四種支援格式的其中一種，則不限制可寫入的資料量和資料類型。  
  
        > [!NOTE]
        >  除了明確寫入的資料以及 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 實作的透通資料以外，設定 API 也會儲存 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本資訊。 儲存的設定可以針對設定匯入期間產生它們的 IDE 版本進行比較。  
  
## 範例  
 下列範例示範如何匯入和匯出設定資料。  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## 請參閱  
 [使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)   
 [擴充使用者設定和選項](../Topic/Extending%20User%20Settings%20and%20Options.md)   
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [如何：使用 Interop 組件匯入設定](../misc/how-to-use-interop-assemblies-to-import-settings.md)