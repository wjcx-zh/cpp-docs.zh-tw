---
title: "匯入設定 | Microsoft Docs"
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
  - "使用者設定 [Visual Studio SDK], 使用 Managed 封裝架構匯入"
  - "IDE 設定, 使用 Managed 封裝架構匯入"
  - "IDE, 使用 Managed 封裝架構匯入設定"
  - "Managed 封裝架構, 匯入環境設定"
ms.assetid: 943f9a5b-c5a5-45ce-a5a9-8d4c02f15577
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 匯入設定
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 會使用可實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 介面並註冊以支援 VSPackage 實作的類別。 這項實作用來擷取 VSPackage 的狀態。  
  
 因為 IDE 會具現化可實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 介面以支援 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 設定的類別，所以應該在獨立的類別中實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 介面。  
  
> [!NOTE]
>  請不要在可實作 <xref:Microsoft.VisualStudio.Shell.Package> 的類別上實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager>。  
  
### 實作設定匯出  
  
1.  宣告可實作 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 設定的類別。  
  
     將類別宣告為實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager>，並使用 `GUID` 來提供它。  
  
    > [!NOTE]
    >  實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 介面的類別也必須實作 <xref:System.ComponentModel.IComponent> 介面，這可以從 <xref:System.ComponentModel.Component> 類別衍生此類別來達成。  
  
     例如:  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  確定可實作設定的類別會從磁碟擷取狀態資料。  
  
     此步驟的執行方式是實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 方法。  
  
     要持續保存的確切資訊以及如何從 VSPackage 取得和封送處理該資訊，每個 VSPackage 都不同。  
  
     不論要由 VSPackage 持續保存的資訊為何，實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 的類別必須使用所提供的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 介面來擷取設定檔案中的資料。  
  
     一般而言，與下列的範例相同，<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 也會驗證擷取的資料，並更新 VSPackage 的狀態。  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        Dim value As String   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        reader.ReadSettingString("PbrsShowDesc", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Help Visibility Setting")   
        Else   
            myState.HelpVisible = Not value.Equals("0")   
        End If   
        reader.ReadSettingString("PbrsAlpha", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Retrieve Sort Value")   
        Else   
            If Not value.Equals("0") Then   
                myState.SortState = SortState.Alphabetical   
            Else   
                myState.SortState = SortState.Categorized   
            End If   
        End If   
    End If  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
    if (mySvc != null){  
      string value;  
      StateObject myState = mySvc.MyPackage.packageState;  
      reader.ReadSettingString("PbrsShowDesc", out value);  
      if (value == null || value == ""){  
          reader.ReportError("Unable to Help Visibility Setting");  
      }else{  
          myState.HelpVisible = !value.Equals("0");  
      }  
      reader.ReadSettingString("PbrsAlpha", out value);  
      if (value == null || value == ""){  
          reader.ReportError("Unable to Retrieve Sort Value");  
      }else{  
        if (!value.Equals("0")){  
          myState.SortState = SortState.Alphabetical;  
        }else{  
          myState.SortState = SortState.Categorized;  
        }  
      }  
    }  
    ```  
  
     實作詳細資料：  
  
    -   使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 介面的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A> 方法，透過 IDE 以互動方式將錯誤回報給使用者：  
  
        ```vb#  
        reader.ReadSettingString("PbrsAlpha", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Retrieve Sort Value")   
        End If  
        ```  
  
        ```c#  
          reader.ReadSettingString("PbrsAlpha", out value);  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }  
        ```  
  
    -   實際擷取所儲存設定之前，<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 方法的實作應該使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> 方法確認支援匯出所儲存設定的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本。  
  
         在下列的範例中，實作會確認主要版本號碼為 `m_supportVer` 的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本是否已產生設定，如果為否，則發出錯誤訊號。  
  
        ```vb#  
        If pnMajor <> m_supportVer Then   
            reader.ReportError("Unsupported Version")   
        End If  
        ```  
  
        ```c#  
        if (pnMajor != m_supportVer){  
          reader.ReportError("Unsupported Version");  
        }  
        ```  
  
    -   [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 設定檔支援隨機資料存取，因此讀取和寫入器設定作業的順序不重要。 在下列範例中，<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法實作中的寫入器作業順序與 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 方法中的讀取作業相反。  
  
    -   提供給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 介面之方法的 `pszSettingName` 引數值必須唯一識別設定類別內所儲存的每個資料項目。  
  
        > [!NOTE]
        >  因為 IDE 使用可實作設定之類別的 GUID 以及 `pszSettingName` 的值來識別每個儲存的設定，所以名稱在實作類別範圍內只能是唯一的。 如果使用相同的 `pszSettingName` 值來呼叫多個 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 方法，則會覆寫設定檔案中的原始值。  
  
3.  請確定 VSPackage 狀態與本機儲存或快取的設定之間的連貫性。  
  
     這個步驟通常是在 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法實作期間執行 \(如下列範例所示\)。 這個步驟的詳細資料僅適用於 VSPackage，而且可能包含從 Automation 取得 VSPackage 的狀態、查詢 VSPackage，以及設定登錄機碼。  
  
    > [!NOTE]
    >  IDE 在初始化所支援的 VSPackage 期間呼叫 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法時，<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法應該擷取 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法所儲存的資訊。  
  
     在下列範例中，提供設定支援的類別會實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法：  
  
    -   存取 VSPackage 的已更新狀態資訊。  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   使用該資訊可更新 VSPackage 的登錄設定。  
  
        ```vb#  
        If mySvc.MyPackage.packageState IsNot Nothing Then   
            Using rootKey   
                Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                    Using pbrsKey   
                        DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                    End Using   
                End Using   
            End Using   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.packageState != null) {  
          using (rootKey) {  
            using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
              using (pbrsKey) {  
                ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
              }  
            }  
          }  
        }  
        ```  
  
    -   > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 與 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法之間的工作區分取決於實作，並且是隨意自訂的。 例如，實作可以改寫為 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法的空白實作，以及在 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法中執行的所有登錄和狀態查詢。  
  
4.  註冊可實作支援 VSPackage 之設定的類別。  
  
     將使用可實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 之類別的 <xref:System.Type> 所建構的 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 執行個體，套用至 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Package> 實作。  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
     [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     在此情況下，屬性會通知 IDE：`MyPackageProfileManager` 類別會將設定實作提供給 `MyPackage` 類別。 在登錄的 HKLM\\Software\\Microsoft\\VisualStudio\\*\<版本\>*\\UserSettings\\ CoreUI\_MyPackage 下會建立自訂設定點，其中 *\<版本\>* 是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的版本 \(例如 8.0\)。  
  
     如需詳細資訊，請參閱 [使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)和 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
## 範例  
 下列範例會對類別實作 <xref:Microsoft.VisualStudio.Shell.IProfileManager>。  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First check if we are getting data from the correct major version.   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First check if we are getting data from the correct major version.   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [匯出設定](../misc/exporting-settings.md)   
 [使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)