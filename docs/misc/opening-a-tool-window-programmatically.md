---
title: "以程式設計方式開啟工具視窗 | Microsoft Docs"
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
  - "工具視窗, 以程式設計方式建立"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 以程式設計方式開啟工具視窗
按一下功能表上的命令，或按對等的鍵盤快速鍵，通常會開啟工具視窗。 不過，您可能必須以程式設計方式開啟工具視窗，就和命令處理常式所做的一樣。  
  
 若要在提供它的受管理 VSPackage 中開啟工具視窗，請使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>。 若要在另一個 VSPackage 中開啟工具視窗，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A>。 在任一情況下，會視需要建立工具視窗。  
  
 下列程式碼是取自 C\# Reference.ToolWindow 範例。  
  
### 以程式設計方式開啟工具視窗  
  
1.  建立工具視窗窗格、框架以及實作它們的 VSPackage。 如需詳細資訊，請參閱[加入工具視窗](../Topic/Adding%20a%20Tool%20Window.md)。  
  
2.  將 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 加入提供它的 VSPackage。  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     這會註冊以停駐形式開啟到**方案總管**的工具視窗 PersistedWindowPane。 如需詳細資訊，請參閱[註冊工具視窗](../Topic/Registering%20a%20Tool%20Window.md)。  
  
3.  使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 尋找工具視窗窗格，或在不存在時建立它。  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  從工具視窗窗格中，取得工具視窗框架。  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  顯示工具視窗。  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```