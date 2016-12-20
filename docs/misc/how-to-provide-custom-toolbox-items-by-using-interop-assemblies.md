---
title: "如何：使用 Interop 組件提供自訂工具箱項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱 [Visual Studio SDK], 使用 Interop 組件加入項目"
ms.assetid: c3e8b404-7086-4e08-9d07-ab9c509963ca
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# 如何：使用 Interop 組件提供自訂工具箱項目
> [!NOTE]
>  在 \[工具箱\] 加入自訂控制項的建議方式是使用隨附於 Visual Studio 10 SDK 的 \[工具箱控制項\] 範本。 本主題僅為回溯相容性以及將現有控制項加入 \[工具箱\] 中之目的而保留。  
>   
>  如需使用範本建立 \[工具箱\] 控制項的詳細資訊，請參閱[如何：建立使用 Windows Forms 的 \[工具箱\] 控制項](../Topic/How%20to:%20Create%20a%20Toolbox%20Control%20That%20Uses%20Windows%20Forms.md) 和 [建立 WPF 工具箱控制項](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)。  
  
 以 Interop 組件為基礎的 VSPackage 可以透過加入 ActiveX 控制項來擴充 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \[工具箱\] 功能。  
  
 如需標準 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \[工具箱\] 及 \[剪貼簿\] 格式的清單，請參閱 [擴充工具箱](../misc/extending-the-toolbox.md)。  
  
 如需 VSPackage 如何使用 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 管理 \[工具箱\] 的資訊，請參閱 [管理工具箱](../misc/managing-the-toolbox.md)。  
  
 如需透過 Automation 管理 \[工具箱\] 的資訊，請參閱 [如何：控制工具箱](../Topic/How%20to:%20Control%20the%20Toolbox.md)。  
  
## 程序  
 除非加入 \[工具箱\] 中之項目的 VSPackage 作為 \[工具箱\] 項目提供者，並提供新格式的實作支援，否則這些項目應該會實作標準 \[工具箱\] \[剪貼簿\] 格式。  
  
#### 實作工具箱控制項  
  
-   由以 Unmanaged 程式碼實作之 VSPackage 所提供的 \[工具箱\] 項目必須實作 `IDataObject` 物件或為 ActiveX 控制項，而環境可以從中取得 `IDataObject` 物件。  
  
     如需實作 `IDataObject` 物件以支援 \[工具箱\] 的詳細資訊，請參閱 <xref:System.Runtime.InteropServices.ComTypes.IDataObject>、<xref:Microsoft.VisualStudio.Shell.Interop.TBXITEMINFO> 和 <xref:System.Runtime.InteropServices.ComTypes.FORMATETC>。  
  
#### 將 Interop 組件控制項加入 \[工具箱\] 中  
  
1.  取得下者的執行個體：  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>，其支援將控制項和區段 \(索引標籤\) 加入 \[工具箱\] 中，以及控制 \[工具箱\] 設定的其他部分。  
  
    2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>，其支援當地語系化和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 設定持續性。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 介面繼承自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> 介面。<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 未衍生自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>也未實作它的方法。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 的取得方式，是使用 `SID_SVsToolbox` 的服務 ID 以在 <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 服務上呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 方法。  
  
     介面 ID `IID_IVSToolbox2` 用來取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>，而介面 ID `IID_IVSToolbox3` 會傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>。  
  
     在下列範例中，於 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 介面上呼叫 `QueryInterface`，以使用 `QueryService` 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 介面來取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 介面。  
  
    ```cpp  
    extern CComModule _Module;  
    CComPtr<IVsToolbox2> srpTbx2;  
    CComPtr<IVsToolbox3> srpTbx3;  
    hr = _Module.QueryService(SID_SVsToolbox, IID_IVsToolbox2, (void**) &srpTbx2));  
    hr = srpTbx2->QueryInterface( IID_IVsToolbox3, (void **)&srpTbx3)  
    ```  
  
2.  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 介面的執行個體，以將索引標籤 \(區段\) 和控制項加入 \[工具箱\] 中。  
  
     在下列範例中，會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.AddTab%2A> 方法加入具有當地語系化名稱的新索引標籤。  
  
     因為這個當地語系化名稱為非變異的，所以非當地語系化的非變異名稱 \(在此情況下，是 `L"HTML"`\) 是透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> 方法所設定。  
  
     如果工具箱索引標籤已經存在，則 `AddTab2` 會傳回 E\_FAIL，在此情況下，假設已在嘗試擷取非變異名稱之前適當地加入索引標籤。  
  
     如果已成功加入索引標籤，則 <xref:System.Runtime.InteropServices.ComTypes.IDataObject> 控制項會加入 \[工具箱\] 中；否則會傳回錯誤。  
  
    ```cpp  
    CComBSTR sbstrID;  
    hr = srpTbx2->AddTab2((WCHAR*)szwDisplayTabName, *pclsidPackage);  
    if ( hr == S_OK) {  
        sbstrID =L"HTML";  
        hr = srpTbx3->SetIDOfTab( (WCHAR*)szwDisplayTabName, sbstrID);  
    }else{  
        hr = S_OK;  
        hr = srpTbx3->GetIDOfTab( (WCHAR*)szwDisplayTabName, &sbstrID );  
  
    }  
    if ( hr = S_OK){  
        hr=srpTbx2->AddItem(tbxItem, &tinfo, bstrLabel);  
    }  
    return hr;  
    ```  
  
 除了加入 \[工具箱\] 本身之外，VSPackage 還可以設定為 \[工具箱\] 資料提供者，而且可以用來將拖放支援擴充至 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE。 這可將任意的剪貼簿格式公開給 \[工具箱\] 和編輯器。  
  
#### 將 VSPackage 設定為工具箱項目提供者  
  
1.  將 Interop VSPackage 註冊為 \[工具箱\] 項目提供者。  
  
     如需註冊為 \[工具箱\] 提供者的詳細資訊，請參閱 [註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)。  
  
2.  註冊為支援自訂 \[工具箱\] \[剪貼簿\] 格式。  
  
     支援未實作所有標準 \[工具箱\] \[剪貼簿\] 格式或實作自訂 \[工具箱\] \[剪貼簿\] 格式之控制項的 Interop VSPackage 必須：  
  
    1.  註冊所支援的 \[工具箱\] \[剪貼簿\] 格式。 如需詳細資訊，請參閱[註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)。  
  
    2.  建立可實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> 介面的類別。  
  
        > [!NOTE]
        >  不應該在實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 介面的相同類別上實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> 介面。  
  
    3.  以程式設計方式通知 \[工具箱\]：<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> 介面的特定實作會透過其中一種對等方法來支援自訂資料格式 － <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry.RegisterDataProvider%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A>。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A> 方法的呼叫一般是在 VSPackage 變成使用中時，透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 方法的實作或 <xref:Microsoft.VisualStudio.Shell.WindowPane.OnCreate%2A> 處理常式方法來達成。  
  
        ```cpp  
        CComPtr<IVsToolboxDataProviderRegistry> pTB;  
        if (SUCCEEDED (hr = pServiceProvider->QueryService(SID_SVsToolboxDataProviderRegistry, IID_IVsToolboxDataProviderRegistry, (PVOID*)&pTB)) && pTB != NULL)  
        {  
            CustToolboxDataProvider* pDP = new CustToolboxDataProvider;  
            if (pDP)  
            {  
                pDP->AddRef();  
                VSCOOKIE dwDPCookie; //UNDONE: pass NULL instead of ptr to the cookie when RegisterDataProvider allows it.  
                pTB->RegisterDataProvider((IVsToolboxDataProvider*)pDP, &dwDPCookie);  
                pDP->Release();  
            }  
            else  
            {  
                hr = E_OUTOFMEMORY;  
            }  
        }  
        ```  
  
 如需標準 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \[工具箱\] \[剪貼簿\] 格式的清單，請參閱　[擴充工具箱](../misc/extending-the-toolbox.md)。  
  
## 請參閱  
 [擴充工具箱](../misc/extending-the-toolbox.md)   
 [工具箱逐步解說](../misc/toolbox-walkthroughs.md)   
 [註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)   
 [進階工具箱控制項開發](../misc/advanced-toolbox-control-development.md)   
 [管理工具箱](../misc/managing-the-toolbox.md)   
 [如何：控制工具箱](../Topic/How%20to:%20Control%20the%20Toolbox.md)