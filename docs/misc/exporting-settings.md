---
title: "匯出設定 | Microsoft Docs"
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
  - "IDE, 使用 Managed 封裝架構匯出設定"
  - "Managed 封裝架構, 匯出環境設定"
  - "使用者設定 [Visual Studio SDK], 使用 Managed 封裝架構匯出"
  - "IDE 設定, 使用 Managed 封裝架構匯出"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# 匯出設定
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\) 會使用類別來實作<xref:Microsoft.VisualStudio.Shell.IProfileManager>介面和類別，已經註冊為支援特定的 VSPackage 實作儲存 VSPackage 狀態。  
  
 因為 IDE 會具現化之類別的實作<xref:Microsoft.VisualStudio.Shell.IProfileManager>介面，以支援設定的<xref:Microsoft.VisualStudio.Shell.IProfileManager>應該獨立的類別中實作。  
  
> [!NOTE]
>  不會實作<xref:Microsoft.VisualStudio.Shell.IProfileManager>上實作的類別<xref:Microsoft.VisualStudio.Shell.Package>。  
  
### 若要實作的設定匯出  
  
1.  宣告實作的類別[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定。  
  
     宣告和實作類別<xref:Microsoft.VisualStudio.Shell.IProfileManager>介面，並且在提供 GUID。  
  
    > [!NOTE]
    >  類別的實作<xref:Microsoft.VisualStudio.Shell.IProfileManager>也必須實作<xref:System.ComponentModel.IComponent>。  這可以藉由衍生的類別<xref:System.ComponentModel.Component>。  
  
     例如：  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  請確定實作設定的類別會取得正確的狀態資訊。  此程序專屬於每個 VSPackage，並可能牽涉到從自動化取得狀態、 查詢登錄機碼或查詢的 VSPackage。  
  
     一般而言，請按照下列的範例中，使用的實作<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>方法來驗證，並接移 VSPackage 狀態資訊。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>初始化它支援 VSPackage 時，ide 也呼叫方法。  
  
     在此情況下，實作<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>方法可以執行下列操作：  
  
    -   取得在 VSPackage 的目前設定的狀態資訊，並儲存在登錄中的組態資訊的存取。  
  
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
  
    -   取決於所傳回的值`MakeCurrentSettingTheDefault` VSPackage 方法，它會是更新登錄設定登錄設定值，使用目前的 VSPackage 狀態，或是狀態。  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         為了簡單起見，在這個範例中，除非`MakeCurrentSettingsTheDefault`方法傳回`true`，目前的狀態永遠重設為預設值儲存在登錄中。  
  
3.  請確定實作設定的類別也會持續存在磁碟的狀態。  
  
     實際的寫入的狀態資訊的設定檔都必須由類別實作， <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>方法。  設定寫入作業的特定內容視實作而定。  
  
     然而，類別必須取得狀態資訊的存取權，必須使用所提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>介面，以將資料儲存至設定檔。  
  
     一般而言，如下例所示，實作<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>方法並不會驗證狀態資訊。  在執行驗證<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>方法。  相反地，實作只取得狀態資訊的存取權，並寫入，如此一來，以字串資料。  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     實作詳細資料如下所示：  
  
    -   除了明確的書面且根本不需要的資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>方法實作中，設定 API 也會儲存[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]版本資訊。  因此，儲存的設定可以比較這些設定匯入作業期間所產生的 ide 版本。  
  
    -   值為`pszSettingName`引數提供給方法的<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>介面必須唯一地識別儲存某個設定分類在各資料元素。  
  
        > [!NOTE]
        >  名稱必須只有唯一的實作類別範圍內。  IDE 會使用實作的設定類別的 GUID 及值`pszSettingName`來識別每一個儲存設定。  如果多個<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>都具有相同的方法`pszSettingName`的值都稱為、 原始值會覆寫設定檔中。  
  
    -   設定檔支援隨機資料存取，因此順序讀取及寫入作業並不重要。  在下列範例中，寫入器的實作中的作業順序的<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>方法是相反的讀取作業，在<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>方法。  
  
    -   如果實作可以將資料對應到其中一個四個支援的格式，再沒有任何限制，有關的多，或可以撰寫哪些類型的資料。  
  
        > [!NOTE]
        >  人力資源之間的<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>和<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>方法的實作而定，而且是隨意訂定。  比方說，實作可以重新撰寫使用空的實作<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>方法，讓所有的登錄和狀態查詢執行的<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>方法。  
  
4.  暫存器的實作類別做為對 VSPackage 提供支援的設定。  
  
     套用的執行個體<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> ，藉由使用建構<xref:System.Type>實作的類別的<xref:Microsoft.VisualStudio.Shell.IProfileManager>到 VSPackage <xref:Microsoft.VisualStudio.Shell.Package>實作。  
  
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
  
     在此情況下，屬性會通知 IDE 的`MyPackageProfileManager`類別會提供要設定實作`MyPackage`類別。  自訂設定在登錄中建立點下 HKLM\\Software\\Microsoft\\VisualStudio\\*版本*\\UserSettings\\ CoreUI\_MyPackage，其中*版本*版本的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，比方說，10.0。  
  
     如需詳細資訊，請參閱 [使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)和 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
## 範例  
 下列範例會實作<xref:Microsoft.VisualStudio.Shell.IProfileManager>在類別上。  
  
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
            ' First, check if data is obtained from the correct major version   
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
  
Convert C# to VB.NET  
  
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
      // First, check if data is obtained from the correct major version   
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
 [匯入設定](../misc/importing-settings.md)   
 [使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)