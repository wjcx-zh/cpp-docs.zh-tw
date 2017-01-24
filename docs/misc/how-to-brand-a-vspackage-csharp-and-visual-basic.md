---
title: "如何：設定 VSPackage 的品牌 (C# 和 Visual Basic) | Microsoft Docs"
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
  - "關於對話方塊"
  - "VSPackage, 啟動顯示畫面"
  - "VSPackage, 品牌"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 如何：設定 VSPackage 的品牌 (C# 和 Visual Basic)
若要顯示在**有關**對話方塊並啟動顯示畫面，就必須實作 VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>介面。  這會提供下列資訊，以[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]：  
  
-   名稱  
  
-   識別碼，如序列連接埠或版本號碼  
  
-   資訊  
  
-   標誌的圖示  
  
 下列程式碼是從[VSSDK 範例](../misc/vssdk-samples.md)。  
  
### 若要實作 IVsInstalledProduct 介面  
  
1.  新增<xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute>屬性設定為實作 VSPackage 的類別。  這個類別必須衍生自兩者<xref:Microsoft.VisualStudio.Shell.Package>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>。  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     第一個引數中， <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>的<xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute>屬性可以告訴我們[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>以取得產品資訊，而不是 InstalledProducts 登錄機碼。  其餘的引數選取來分別顯示產品名稱\]、 \[詳細資料\] 及 \[識別碼的字串資源。  不過，因為第一個引數是`true`，其餘的引數是`null`。  
  
2.  以滑鼠右鍵按一下<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>，指到**實作介面**，然後按一下 \[ **實作介面**。  
  
3.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>藉由使用下列程式碼。  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]呼叫這些方法來取得商標 VSPackage 的資訊。  GetResourceString 方法用來將當地語系化的這項資訊。  
  
    > [!NOTE]
    >  為了簡單起見，程式碼註解會被刪除。  您可以找到它們在[VSSDK 範例](../misc/vssdk-samples.md)。  
  
### 若要維護產品資訊的字串  
  
1.  按兩下 VSPackage 相關聯的資源.resx 檔案。  
  
     資源編輯器隨即開啟。  
  
2.  尋找或加入產品名稱資訊，和編號。  
  
     下列的資源字串是來自[VSSDK 範例](../misc/vssdk-samples.md)。  
  
     @101  
     套件啟動顯示畫面和說明有關正式名稱 \(C\#\)。  
  
     @102  
     此套件會示範如何顯示文字和影像在開頭顯示畫面和相關說明。  
  
     @104  
     8.0  
  
3.  選取並視需要編輯這項資訊。  
  
### 若要維護產品的圖示和點陣圖  
  
1.  將點陣圖與圖示加入專案當做專案資源。  
  
     如需詳細資訊，請參閱 [NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/zh-tw/95f15d03-bed0-410c-8d1f-dece5199ba1e)。  
  
2.  關閉資源編輯器並重新開啟在 XML 或文字編輯器中的.resx 檔案。  
  
    > [!NOTE]
    >  資源編輯器不支援將識別碼指派給項目不是字串。  
  
3.  尋找或加入.resx 檔中的圖示和點陣圖資源。  下列的資源是從[VSSDK 範例](../misc/vssdk-samples.md)。  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### 若要測試的關於對話方塊\] 方塊中，啟動顯示畫面  
  
-   若要測試您的 VSPackage，請參閱[如何：測試相關說明和啟動顯示畫面](../misc/how-to-test-the-help-about-and-splash-screens.md)。  
  
## 請參閱  
 [VSPackage 品牌](../misc/vspackage-branding.md)