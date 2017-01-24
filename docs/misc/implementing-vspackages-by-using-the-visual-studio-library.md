---
title: "使用 Visual Studio 程式庫實作 VSPackage | Microsoft Docs"
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
  - "Visual Studio 程式庫, 實作 VSPackage"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# 使用 Visual Studio 程式庫實作 VSPackage
`IVsPackageImpl` Visual Studio 的媒體櫃中的類別會提供最少實作的<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>介面。  `IVsPackageImpl`大部分的維護方法會處理<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。  您可能需要提供有意義的實作會覆寫其他方法包括：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]封裝範本會產生此處所討論的所有程式碼。  您可以使用範本來為您產生的 VSPackage，以節省時間。  
  
 使用 Visual Studio 程式庫通常會實作的封裝會將 VSPackage 類別繼承 ATL 的[CComObjectRootEx Class](../atl/reference/ccomobjectrootex-class.md)和[CComCoClass Class](../atl/reference/ccomcoclass-class.md)和 Visual Studio 程式庫的 IVsPackageImpl。  例如，以下是從 Reference.Package 範例的 VSPackage 類別宣告：  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 `IVsPackageImpl` VSPackage 類別本身，並找出 VSPackage 的 GUID 的指標，會顯示的樣板參數。  
  
## 支援與 COM 對應的 QueryInterface  
 若要取得 ATL 的支援`QueryInterface`，它的 COM 對應必須列出類別會實作的介面。  比方說下, 面是 Reference.Package 範例中的 VSPackage 類別的 COM 對應：  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 如需有關 COM 對應的詳細資訊，請參閱[Implementing CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)和[COM\_INTERFACE\_ENTRY Macros](../Topic/COM_INTERFACE_ENTRY%20Macros.md)。  
  
## 支援與登錄對應的登錄  
 Visual Studio 的程式庫使用 ATL 樣式。RGS 檔支援的 COM 物件的登錄。  為了支援語彙基元中的取代。RGS 檔，Visual Studio 程式庫使用登錄對應。  登錄對應的清單中的符號，來取代，並支援使用 Id 的字串資料表資源。  
  
 比方說下, 面是 Reference.Package 範例中的 VSPackage 類別的登錄對應：  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## 請參閱  
 [VSSDK 範例](../misc/vssdk-samples.md)