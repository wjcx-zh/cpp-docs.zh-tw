---
title: "進階工具箱控制項開發 | Microsoft Docs"
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
  - "工具箱 [Visual Studio SDK], 使用 MPF 加入項目"
ms.assetid: d22479a8-6d95-400c-a115-f46d10c10d2f
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# 進階工具箱控制項開發
> [!NOTE]
>  若要將自訂控制項加入至 \[工具箱\] 中的建議的方式是使用 Visual Studio 的 10 SDK 隨附的工具箱控制項樣板。  本主題被保留用於回溯相容性、 將現有的控制項加入至 \[工具箱\] 中，以及進階的工具箱控制項開發。  
>   
>  如需有關如何使用範本建立工具箱控制項的詳細資訊，請參閱[如何：建立使用 Windows Forms 的 \[工具箱\] 控制項](../Topic/How%20to:%20Create%20a%20Toolbox%20Control%20That%20Uses%20Windows%20Forms.md)和[建立 WPF 工具箱控制項](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)。  
  
 可擴充的管理套件架構為基礎的 VSPackage [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]工具箱加入控制項的功能，物件衍生自<xref:System.Drawing.Design.ToolboxItem>物件。  每個<xref:System.Drawing.Design.ToolboxItem>由衍生自物件實作<xref:System.ComponentModel.Component>。  
  
## 工具箱項目提供者的 VSPackage  
 管理套件架構為基礎的 VSPackage 必須將自己登錄為工具箱控制提供者，透過[!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)]屬性，並處理工具箱相關的事件。  
  
#### 若要將 VSPackage 設定為工具箱項目提供者  
  
1.  建立執行個體的<xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>套用至類別實作<xref:Microsoft.VisualStudio.Shell.Package>。  例如：  
  
    ```vb#  
    Namespace Vsip.LoadToolboxMembers   
        <ProvideToolboxItems(14)> _   
        <DefaultRegistryRoot("Software\Microsoft\VisualStudio\8.0")> _   
        <InstalledProductRegistration(False, "#100", "#102", "1.0", IconResourceID := 400)> _   
        <ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)> _   
        <ProvideMenuResource(1000, 1)> _   
        <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
        Public Class LoadToolboxMembers   
            Inherits Package   
        End Class   
    End Namespace  
    ```  
  
    ```c#  
    namespace Vsip.LoadToolboxMembers {  
        [ProvideToolboxItems(14)]  
        [DefaultRegistryRoot("Software\\Microsoft\\VisualStudio\\8.0")]  
        [InstalledProductRegistration(false, "#100", "#102", "1.0", IconResourceID = 400)]  
        [ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)]  
        [ProvideMenuResource(1000, 1)]  
        [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
        public class LoadToolboxMembers : Package {  
    ```  
  
    > [!NOTE]
    >  建構函式<xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>會做為引數的整數版本號碼。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]環境使用這個版本號碼，來判斷 VSPackage，提供<xref:System.Drawing.Design.ToolboxItem>物件就必須重新載入，或如果快取的資訊可供 \[工具箱\] 中。  若要保證提供時，重新載入的 VSPackage <xref:System.Drawing.Design.ToolboxItem> ，仍在開發、 恆增加任何修改之後的這個版本號碼。  
  
2.  如果<xref:System.Drawing.Design.ToolboxItem>物件提供非標準的工具箱剪貼簿格式，執行個體的<xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute>必須套用至類別實作<xref:Microsoft.VisualStudio.Shell.Package>物件支援的每一種剪貼簿格式的<xref:System.Drawing.Design.ToolboxItem> VSPackage 所提供的物件。  
  
     如需有關支援的工具箱剪貼簿格式的詳細資訊，請參閱[擴充工具箱](../misc/extending-the-toolbox.md)。  
  
    > [!NOTE]
    >  如果 VSPackage 指出它會提供任何<xref:System.Drawing.Design.ToolboxItem>具有非標準的剪貼簿格式，物件[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]環境假設只有所指示的格式<xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute>執行個體套用至 VSPackage <xref:Microsoft.VisualStudio.Shell.Package>類別實作所支援的 VSPackage。  如果 VSPackage，就必須支援預設的剪貼簿格式，以及非標準的格式，它必須套用的執行個體<xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute>的每個預設的格式，以及非標準的格式。  
  
3.  如果 VSPackage 提供的動態組態<xref:System.Drawing.Design.ToolboxItem>，則它必須：  
  
    1.  套用的執行個體<xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>使用建構<xref:System.Type>封裝用來實作<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>介面。  
  
    2.  在`public`類別不受影響的 VSPackage <xref:Microsoft.VisualStudio.Shell.Package>，VSPackage 必須實作<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>介面。  
  
         執行個體的<xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>必須套用至類別實作<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>，使用字串，包含做為引數的選取條件 \(篩選\) <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>執行個體的建構函式。  
  
 如需如何告知[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] VSPackage 提供工具箱的環境會控制，請參閱[註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)。  
  
 如需範例，說明如何實作其中一個<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>支援，請參閱[逐步解說：以動態方式自訂工具箱項目設定](../misc/walkthrough-customizing-toolbox-item-configuration-dynamically.md)。  
  
1.  提供 VSPackages <xref:System.Drawing.Design.ToolboxItem>必須處理<xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>和<xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>事件。  
  
    1.  實作處理常式的<xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>和<xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>事件：  
  
        ```vb#  
        Private Sub OnToolboxUpgraded(ByVal sender As Object, ByVal e As EventArgs)   
            OnToolboxInitialized(send, e)   
        End Sub   
        Private Sub OnToolboxInitialized(ByVal sender As Object, ByVal e As EventArgs)   
            'Make sure all toolbox items are added.   
        End Sub  
        ```  
  
        ```c#  
        private void OnToolboxUpgraded(object sender, EventArgs e) {  
            OnToolboxInitialized(send,e);  
        }  
        private void OnToolboxInitialized(object sender, EventArgs e) {  
            //Make sure all toolbox items are added.  
        }  
        ```  
  
    2.  訂閱<xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>和<xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>事件。  
  
         尤其是<xref:Microsoft.VisualStudio.Shell.Package>實作的<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法：  
  
        ```vb#  
        Protected Overloads Overrides Sub Initialize()   
            AddHandler ToolboxInitialized, AddressOf OnToolboxInitialized   
            AddHandler ToolboxUpgraded, AddressOf OnToolboxUpgraded   
        End Sub  
        ```  
  
        ```c#  
        protected override void Initialize() {  
            ToolboxInitialized += new EventHandler(OnToolboxInitialized);  
            ToolboxUpgraded += new EventHandler(OnToolboxUpgraded);  
        }  
        ```  
  
     如需如何實作處理常式的範例<xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>和<xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>事件，請參閱[逐步解說：自動載入工具箱項目](../misc/walkthrough-autoloading-toolbox-items.md)。  
  
## 建立工具箱控制項  
 工具箱控制項的基礎實作必須衍生自<xref:System.ComponentModel.Component> ，封裝預設值，或是衍生程度的實作在<xref:System.Drawing.Design.ToolboxItem>物件。  
  
 最簡單的方法，以提供<xref:System.ComponentModel.Component>\-工具箱控制項衍生程度的實作是由擴充衍生自物件<xref:System.Windows.Forms.Control>，特別是， <xref:System.Windows.Forms.UserControl>類別。  
  
#### 若要建立工具箱控制項  
  
1.  使用**方案總管\] 中**的**加入新項目**命令，以建立工具箱物件實作<xref:System.Windows.Forms.UserControl>。  
  
    ```vb#  
    Public Partial Class ToolboxControl1   
        Inherits UserControl   
        Public Sub New()   
            InitializeComponent()   
        End Sub   
        Private Sub button1_Click(ByVal sender As Object, ByVal e As EventArgs)   
            MsgBox("Hello world from" & Me.ToString())   
        End Sub   
  
        Private Sub ToolboxItem1_Load(ByVal sender As Object, ByVal e As EventArgs)   
  
        End Sub   
    End Class  
    ```  
  
    ```c#  
    public partial class ToolboxControl1 : UserControl {  
            public ToolboxControl1() {  
                InitializeComponent();  
            }  
  
            private void button1_Click(object sender, EventArgs e) {  
                MessageBox.Show("Hello world from" + this.ToString());  
            }  
  
            private void ToolboxItem1_Load(object sender, EventArgs e) {  
  
            }  
        }  
    ```  
  
     如需有關如何撰寫 Windows Form 控制項與工具箱控制項的詳細資訊，請參閱[使用 .NET Framework 開發自訂的 Windows Form 控制項](../Topic/Developing%20Custom%20Windows%20Forms%20Controls%20with%20the%20.NET%20Framework.md)或[逐步解說：自動載入工具箱項目](../misc/walkthrough-autoloading-toolbox-items.md)。  
  
2.  \(選擇性\)應用程式可以選擇使用自訂物件衍生自<xref:System.Drawing.Design.ToolboxItem>物件，以提供其工具箱控制項**工具箱**。  
  
    > [!NOTE]
    >  任何類別衍生自<xref:System.Drawing.Design.ToolboxItem>物件必須要有執行個體的<xref:System.SerializableAttribute>套用到它。  
  
     自訂的實作衍生自<xref:System.Drawing.Design.ToolboxItem>可以擴充應用程式提供更多的控制方式<xref:System.Drawing.Design.ToolboxItem>資料序列化、 增強的設計工具的中繼資料的處理，支援非標準的剪貼簿格式，並可讓一般使用者的互動功能。  
  
     在範例中，對話方塊會提示使用者選取的功能：  
  
    ```vb#  
    <ToolboxItemAttribute(GetType(CustomControl))> _   
    <Serializable()> _   
    Class CustomControl   
        Inherits ToolboxItem   
  
        Public Sub New(ByVal type As Type)   
            MyBase.New(GetType(CustomControl))   
        End Sub   
        Public Sub New(ByVal type As Type, ByVal icon As Bitmap)   
            MyBase.New(GetType(SCustomControl))   
            Me.DisplayName = "CustomContorl"   
            Me.Bitmap = icon   
        End Sub   
  
        Private Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)   
            Deserialize(info, context)   
        End Sub   
        Protected Overloads Overrides Function CreateComponentsCore(ByVal host As IDesignerHost) As IComponent()   
            Dim dialog As New CustomControlDialog(host)   
            Dim dialogResult__1 As DialogResult = dialog.ShowDialog()   
            If dialogResult__1 = DialogResult.OK Then   
                Dim component As IComponent = DirectCast(dialog.CustomInstance, IComponent)   
                Dim container As IContainer = host.Container   
                container.Add(component)   
                Return New IComponent() {component}   
            Else   
                Return New IComponent() {}   
            End If   
        End Function   
    End Class  
    ```  
  
    ```c#  
    [ToolboxItemAttribute(typeof(CustomControl))]  
    [Serializable]  
    class CustomControl : ToolboxItem {  
  
        public CustomControl(Type type) : base(typeof(CustomControl)) {}  
            public CustomControl(Type type, Bitmap icon) : base(typeof(SCustomControl)) {  
            this.DisplayName = "CustomContorl";  
            this.Bitmap = icon;  
        }  
  
        private CustomControl(SerializationInfo info, StreamingContext context) {  
            Deserialize(info, context);  
        }  
        protected override IComponent[] CreateComponentsCore(IDesignerHost host) {  
            CustomControlDialog dialog = new CustomControlDialog(host);  
            DialogResult dialogResult = dialog.ShowDialog();  
            if (dialogResult == DialogResult.OK) {  
                IComponent component = (IComponent)dialog.CustomInstance;  
                IContainer container = host.Container;  
                container.Add(component);  
                return new IComponent[] { component };  
            }  
            else {  
                return new IComponent[] {};  
            }  
        }  
    }  
    ```  
  
> [!NOTE]
>  您也可為一個類別衍生自<xref:System.Drawing.Design.ToolboxItem>物件，以提供自己的獨立的實作的基礎控制項。  該類別是負責建立和提供所有的基礎元件。  
  
## 明確的額外的工具箱項目  
 要加入至 \[工具箱\] 中，控制項必須位於執行個體的<xref:System.Drawing.Design.ToolboxItem>或衍生自物件的<xref:System.Drawing.Design.ToolboxItem> ，然後加入**工具箱**使用<xref:System.Drawing.Design.IToolboxService>介面。  
  
#### 若要封裝和加入工具箱控制項  
  
1.  封裝<xref:System.ComponentModel.Component>的執行個體中的實作<xref:System.Drawing.Design.ToolboxItem>物件或<xref:System.Drawing.Design.ToolboxItem>\-藉由呼叫該物件的衍生物件<xref:System.Drawing.Design.ToolboxItem.Initialize%2A>與實作元件的方法<xref:System.Type?displayProperty=fullName>：  
  
    ```vb#  
    Dim customItem As New ToolboxItem()   
    If customItem IsNot Nothing Then   
        customItem.Initialize(userControl)   
    End If  
    ```  
  
    ```c#  
    ToolboxItem customItem = new ToolboxItem() ;  
    if (customItem != null) {  
        customItem.Initialize(userControl);  
    }  
    ```  
  
     以上所述是物件的範例`userControl`衍生自<xref:System.Windows.Forms.UserControl> \(執行個體的`ToolboxControl1`如上所示的物件\) 用來建構新的<xref:System.Drawing.Design.ToolboxItem>。  
  
    > [!NOTE]
    >  預設實作<xref:System.Drawing.Design.ToolboxItem>建構函式製作<xref:System.Type?displayProperty=fullName>引數 \(<xref:System.Drawing.Design.ToolboxItem.%23ctor%28System.Type%29>建構函式呼叫<xref:System.Drawing.Design.ToolboxItem>物件的<xref:System.Drawing.Design.ToolboxItem.Initialize%2A>方法。  
  
2.  使用工具箱服務 \(<xref:System.Drawing.Design.IToolboxService>\) 來新增<xref:System.Drawing.Design.ToolboxItem>從基礎的控制項實作建構的物件。  
  
     在下面範例中，存取工具箱服務取得時，部分的屬性<xref:System.Drawing.Design.ToolboxItem>執行個體`customItem`已設定，然後再`customItem`加入至**工具箱**：  
  
    ```vb#  
    Dim toolboxService As IToolboxService = TryCast(GetService(GetType(IToolboxService)), IToolboxService)  
    customItem.Bitmap = New System.Drawing.Bitmap(ToolBoxControl1, "Control1.bmp")  
    customItem.DisplayName = "Custom Item"   
    toolboxService.AddToolboxItem(item, "Custom Tab")  
    ```  
  
    ```c#  
    IToolboxService toolboxService = GetService(typeof(IToolboxService)) as IToolboxService;  
    customItem.Bitmap = new System.Drawing.Bitmap(ToolboxControl1,"Control1.bmp");  
    customItem.DisplayName= "Custom Item";  
    toolboxService.AddToolboxItem(item, "Custom Tab");  
    ```  
  
## 使用反映來加入工具箱控制項  
 將屬性套用至類別實作工具箱控制項可讓[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]環境或[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]基礎的應用程式使用反映來自動偵測並適當地加入控制項以**工具箱**。  
  
#### 若要將反映和屬性套用至工具箱控制項  
  
1.  識別用來實作的執行個體的 \[工具箱\] 控制項的所有物件<xref:System.ComponentModel.ToolboxItemAttribute>。  
  
     執行個體的型別<xref:System.ComponentModel.ToolboxItemAttribute>物件將會決定如何<xref:System.Drawing.Design.ToolboxItem>由其建構。  
  
    1.  套用的執行個體<xref:System.ComponentModel.ToolboxItemAttribute>所建構`BOOLEAN`的值`false`物件對該物件無法使用 \[工具箱\] 中經由反映。  
  
         這可以用來找出一個物件，例如<xref:System.Windows.Forms.UserControl>的**工具箱**在開發期間。  
  
    2.  套用的執行個體<xref:System.ComponentModel.ToolboxItemAttribute>所建構`BOOLEAN`的值`true`物件對該物件可以使用 \[工具箱\] 中經由反映，而且需要物件會加入 \[工具箱\] 中使用預設<xref:System.Drawing.Design.ToolboxItem>物件。  
  
    3.  套用的執行個體<xref:System.ComponentModel.ToolboxItemAttribute>所建構<xref:System.Type>衍生自自訂物件的<xref:System.Drawing.Design.ToolboxItem>讓物件可以使用**工具箱**透過反映，而且需要物件會加入 \[工具箱\] 中使用衍生自這個自訂物件<xref:System.Drawing.Design.ToolboxItem>。  
  
2.  指定 \(以[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]環境的反映機制\) 要用來顯示 \[工具箱\] 中的控制項的點陣圖**工具箱**加上的執行個體<xref:System.Drawing.ToolboxBitmapAttribute>工具箱控制項實作。  
  
3.  如有必要，將套用的例項<xref:System.ComponentModel.ToolboxItemFilterAttribute>到<xref:System.Drawing.Design.ToolboxItem>使用反映來以靜態方式將它們標示用於具有相符的屬性之物件的物件。  
  
     在下面範例中，工具箱控制項的實作會有執行個體的<xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>套用，這會讓該控制項用於**工具箱**只有在目前的工作文件時<xref:System.Windows.Forms.UserControl>設計工具  
  
    ```vb#  
    <ToolboxItemFilter(System.Windows.Forms.UserControl, ToolboxItemFilterType.Require)> _   
    <SerializableAttribute()> _   
    <GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class CustomToolboxItem   
        Inherits ToolboxItem   
    End Class  
    ```  
  
    ```c#  
    [ToolboxItemFilter(System.Windows.Forms.UserControl,ToolboxItemFilterType.Require)]  
    [SerializableAttribute()]  //ToolboxItem implementations much has this attribute.  
    [GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class CustomToolboxItem : ToolboxItem   
    ```  
  
 有三種基本的技巧，可使用反映來自動載入<xref:System.Drawing.Design.ToolboxItem>。  
  
### 使用 「 ToolService 」 功能，以擷取工具箱控制項  
 <xref:System.Drawing.Design.ToolboxService> VSPackages 提供靜態<xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>方法，使用反映來掃瞄支援工具箱項目，所有類型的組件，並傳回這些類型的項目。  要傳回的工具箱項目必須：  
  
-   為公用的。  
  
-   實作<xref:System.ComponentModel.IComponent>類別。  
  
-   不是抽象的。  
  
-   有<xref:System.ComponentModel.ToolboxItemAttribute>根據其類型。  
  
-   沒有<xref:System.ComponentModel.ToolboxItemAttribute>設定為 \[ `false`根據其類型  
  
-   不包含泛型參數。  
  
##### 若要取得這份清單  
  
1.  建立執行個體的<xref:System.Reflection.Assembly>參考的組件，是要加以掃描以便查看<xref:System.Drawing.Design.ToolboxItem>物件。  
  
    > [!NOTE]
    >  若要取得的執行個體<xref:System.Reflection.Assembly>目前的組件，請使用靜態方法<xref:System.Reflection.Assembly.GetExecutingAssembly%2A>。  
  
2.  呼叫<xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>、 傳回<xref:System.Collections.ICollection>物件，包含適當的物件清單。  
  
    > [!NOTE]
    >  如果物件在傳回<xref:System.Collections.ICollection>有有效的執行個體的<xref:System.Drawing.ToolboxBitmapAttribute>指派給它的實作， <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>方法會設定<xref:System.Drawing.Design.ToolboxItem>物件的<xref:System.Drawing.Design.ToolboxItem.Bitmap%2A>屬性。  
  
3.  使用<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>以取得存取權<xref:System.Drawing.Design.IToolboxService>，並使用其<xref:System.Drawing.Design.IToolboxService.AddToolboxItem%2A>方法，將項目傳回<xref:System.Collections.ICollection> \[工具箱\] 中的物件。  
  
     下列程式碼會查詢執行的應用程式，並會取得一份所有其<xref:System.Drawing.Design.ToolboxItem>物件，並將它們載入。  如需說明這在執行程式碼範例，請參閱`Initialization`中的方法[逐步解說：以動態方式自訂工具箱項目設定](../misc/walkthrough-customizing-toolbox-item-configuration-dynamically.md)。  
  
    ```vb#  
    Protected ToolboxItemList As ICollection = Nothing  
    ToolboxItemList = ToolboxService.GetToolboxItems(Assembly.GetExecutingAssembly(), "")  
    If ToolboxItemList Is Nothing Then   
        Throw New ApplicationException("Unable to generate a toolbox Items listing for " & [GetType]().FullName)   
    End If   
    Dim toolboxService As IToolboxService = TryCast(GetService(GetType(IToolboxService)), IToolboxService)   
    For Each itemFromList As ToolboxItem In ToolboxItemList   
        toolboxService.AddToolboxItem(itemFromList, CategoryTab)   
    Next  
    ```  
  
    ```c#  
    protected ICollection ToolboxItemList = null;  
    ToolboxItemList = ToolboxService.GetToolboxItems(Assembly.GetExecutingAssembly(), "");  
    if (ToolboxItemList == null){  
        throw new ApplicationException("Unable to generate a toolbox Items listing for "  
    + GetType().FullName);  
    }  
    IToolboxService toolboxService = GetService(typeof(IToolboxService)) as IToolboxService;  
    foreach (ToolboxItem itemFromList in ToolboxItemList){  
        toolboxService.AddToolboxItem(itemFromList, CategoryTab);  
    }  
    ```  
  
### 使用內嵌的文字資源，以自動載入套件工具箱控制項  
 包含格式正確的清單，工具箱控制項的組件中的文字資源可供<xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>能自動載入工具箱控制項，如果適當地格式化。  
  
 文字資源，其中包含要載入的物件清單就會 VSPackage 可以存取組件中。  
  
##### 若要新增，可以使用文字資源組件  
  
1.  在**方案總管\] 中**，以滑鼠右鍵按一下專案。  
  
2.  指向**新增**，然後按一下 \[ **新的項目**。  
  
3.  在**加入新項目** 對話方塊中，選取 **的文字檔** ，並提供一個名稱。  
  
4.  在**方案總管\] 中**，以滑鼠右鍵按一下新建立的文字檔，並設定 **建置動作**屬性為 \[內嵌資源。  
  
     項目**工具箱**要載入的控制項都必須包含實作的類別，包含它的組件名稱的名稱。  
  
     如 \[工具箱\] 的格式資訊會控制內嵌的文字資源項目，請參閱<xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>參考網頁。  
  
5.  設定搜尋路徑包含裝載工具箱控制項物件的組件的檔案。  
  
     <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>用來代表登錄項目 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\ 中所指定的目錄中只搜尋*\<version\>*\\AssemblyFolders，其中 *\<version\>* 是 Visual Studio \(例如，8.0\) 發行的版本號碼。  
  
    > [!NOTE]
    >  根路徑的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>* 與備用的根，當初始化 Visual Studio 殼層時或使用您可以覆寫<xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute>。  如需詳細資訊，請參閱 [命令列參數](../Topic/Command-Line%20Switches%20\(Visual%20Studio%20SDK\).md)。  
  
     如需 AssemblyFolder 登錄項目正確格式的詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>參考網頁。  
  
6.  取得執行個體的<xref:System.IO.TextReader.Synchronized%2A>存取內嵌的資源，而且如果當地語系化支援所需的類別名稱，執行個體的<xref:System.Resources.ResourceManager>，並使用這些來叫用<xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>方法。  
  
    ```vb#  
    Dim rm As New ResourceManager("TbxCategories", Assembly.GetExecutingAssembly())  
    Dim toolboxStream As Stream = TbxItemProvider.[GetType]().Assembly.GetManifestResourceStream("ToolboxItems.txt")  
    If toolboxStream IsNot Nothing Then   
        Using reader As TextReader = New StreamReader(toolboxStream)   
            ParseToolboxResource(reader, rm)   
        End Using   
    End If  
    ```  
  
    ```c#  
    ResourceManager rm = new ResourceManager("TbxCategories", Assembly.GetExecutingAssembly());  
    Stream toolboxStream = TbxItemProvider.GetType().Assembly.GetManifestResourceStream("ToolboxItems.txt");  
    if (toolboxStream != null) {  
        using (TextReader reader = new StreamReader(toolboxStream)) {  
        ParseToolboxResource(reader, rm);  
    }  
    }  
    ```  
  
     上述清單中包含之類別的組件內嵌的資源中所包含的範例中`TbxItemProvider`傳遞至<xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>與`TbxCategories`的字串資源。  
  
     這個方法會搜尋所有列在資源並載入這些值包含在 \[工具箱\] 控制項的 AssemblyFolders 登錄項目\] 下所指定的目錄中的組件的檔案。  
  
    > [!NOTE]
    >  如果工具箱控制項找到<xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>有有效的執行個體的<xref:System.Drawing.ToolboxBitmapAttribute>指派給它的實作， <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>將會設定用來顯示 \[工具箱\] 控制項的點陣圖。  
  
### 明確地使用反映來自動載入套件工具箱控制項  
 如果要明確的相關資訊的查詢組件，它會**工具箱**及其包含的控制項，而不是委派任務給<xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>，其做法。  
  
##### 若要明確地使用反映來自動載入套件工具箱控制項  
  
1.  建立執行個體的<xref:System.Reflection.Assembly>，是要加以掃描以便查看每個組件參考<xref:System.Drawing.Design.ToolboxItem>物件。  
  
    > [!NOTE]
    >  若要取得的執行個體<xref:System.Reflection.Assembly>目前的組件，請使用靜態方法<xref:System.Reflection.Assembly.GetExecutingAssembly%2A>。  
  
2.  每個組件進行掃描，請使用<xref:System.Reflection.Assembly>物件的<xref:System.Reflection.Assembly.GetTypes%2A>方法，以取得每一份<xref:System.Type?displayProperty=fullName>組件中。  
  
3.  請確認型別不是抽象的且支援<xref:System.ComponentModel.IComponent>介面 \(用來執行個體化的 \[工具箱\] 控制項的所有實作<xref:System.Drawing.Design.ToolboxItem>物件必須實作這個介面\)。  
  
4.  取得屬性的<xref:System.Type> ，並使用這項資訊來判斷 VSPackage 希望載入物件。  
  
    > [!NOTE]
    >  雖然在主體中都可建立<xref:System.Drawing.Design.ToolboxItem>獲取<xref:System.ComponentModel.IComponent>介面實作的執行個體沒有<xref:System.ComponentModel.ToolboxItemAttribute>未設定為`false`套用到它時，我們不建議這樣做。  
  
5.  使用<xref:System.Type.GetConstructor%2A>以取得建構函式的<xref:System.Drawing.Design.ToolboxItem>工具箱控制項需要的物件。  
  
6.  建構<xref:System.Drawing.Design.ToolboxItem>物件，並將它們新增至**工具箱**。  
  
 若要查看說明明確使用反映來取得，並自動載入套件 \[工具箱\] 控制項的範例，請參閱`CreateItemList`所述[逐步解說：自動載入工具箱項目](../misc/walkthrough-autoloading-toolbox-items.md)。  
  
## 額外的工具箱控制項設定  
 VSPackage 可以運用的進一步控管何時以及如何顯示工具箱控制項**工具箱**，透過實作<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>，並改用<xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>，以及<xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>。  
  
 套用<xref:System.ComponentModel.ToolboxItemFilterAttribute>類別的執行個體提供只有靜態控制項何時和如何**工具箱**控制項才可以使用。  
  
#### 若要建立工具箱控制項的動態組態支援  
  
1.  建構類別實作<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> VSPackage 的一部分的介面。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>介面不會實作相同的類別會提供 VSPackage 的實作上<xref:Microsoft.VisualStudio.Shell.Package>。  
  
2.  將相關聯的實作<xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>藉由套用的執行個體的特定組件中的物件與<xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>給它。  
  
     下面這個範例會提供動態組態中的工具箱控制項物件組件的`Vsip.*`命名空間和需要某些<xref:System.Drawing.Design.ToolboxItem>物件是可見只用<xref:System.Windows.Forms.UserControl>\-架構設計人員和其他永遠不會顯示與<xref:System.Windows.Forms.UserControl>\-架構設計人員。  
  
    ```vb#  
    <ProvideAssemblyFilterAttribute("Vsip.*, Version=*, Culture=*, PublicKeyToken=*")> _   
    <GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Public NotInheritable Class ToolboxConfig   
        Implements IConfigureToolboxItem   
        Public Sub New()   
        End Sub  
  
        ''' <summary>   
        ''' Adds extra configuration information to this toolbox item.   
        ''' </summary>   
        Public Sub ConfigureToolboxItem(ByVal item As ToolboxItem)   
            If item Is Nothing Then   
                Exit Sub   
            End If   
  
            'hide from .NET Compact Framework on the device designer.   
            Dim newFilter As ToolboxItemFilterAttribute = Nothing   
            If item.TypeName = GetType(ToolboxControl1).ToString() Then   
                newFilter = New ToolboxItemFilterAttribute("System.Windows.Forms.UserControl", ToolboxItemFilterType.Require)   
            ElseIf item.TypeName = GetType(ToolboxControl2).ToString() Then   
  
                newFilter = New ToolboxItemFilterAttribute("System.Windows.Forms.UserControl", ToolboxItemFilterType.Prevent)   
            End If   
            If newFilter IsNot Nothing Then   
                Dim array As New ArrayList()   
                array.Add(newFilter)   
                item.Filter = DirectCast(array.ToArray(GetType(ToolboxItemFilterAttribute)), ToolboxItemFilterAttribute())   
            End If   
        End Sub   
    End Class  
    ```  
  
    ```c#  
    [ProvideAssemblyFilterAttribute("Vsip.*, Version=*, Culture=*, PublicKeyToken=*")]  
        [GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
        public sealed class ToolboxConfig : IConfigureToolboxItem {  
            public ToolboxConfig() {  
            }  
  
            /// <summary>  
            ///     Adds extra configuration information to this toolbox item.  
            /// </summary>  
            public void ConfigureToolboxItem(ToolboxItem item) {  
                if (item == null)  
                    return;  
  
                //hide from .NET Compact Framework  on the device designer.  
                ToolboxItemFilterAttribute newFilter = null;  
                if (item.TypeName == typeof(ToolboxControl1).ToString()) {  
                    newFilter = new ToolboxItemFilterAttribute("System.Windows.Forms.UserControl",  
                                                          ToolboxItemFilterType.Require);  
                }   
                else if (item.TypeName == typeof(ToolboxControl2).ToString()) {  
  
                    newFilter = new ToolboxItemFilterAttribute("System.Windows.Forms.UserControl",  
                                                          ToolboxItemFilterType.Prevent);  
                }  
                if (newFilter != null) {  
                    ArrayList array = new ArrayList();  
                    array.Add(newFilter);  
                    item.Filter = (ToolboxItemFilterAttribute[])  
                            array.ToArray(typeof(ToolboxItemFilterAttribute));  
                }  
            }  
        }  
    }  
    ```  
  
3.  註冊為提供的特定實作的 VSPackage <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>藉由套用的執行個體<xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> VSPackage 實作的<xref:Microsoft.VisualStudio.Shell.Package>。  
  
     下列範例會通知[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]所實作的封裝的環境`Vsip.ItemConfiguration.ItemConfiguration`提供型別的類別`Vsip.ItemConfiguration.ToolboxConfiguration`支援動態<xref:System.Drawing.Design.ToolboxItem>。  
  
    ```vb#  
    <ProvideToolboxItemsAttribute(3)> _   
    <DefaultRegistryRoot("Software\Microsoft\VisualStudio\8.0")> _   
    <InstalledProductRegistration(False, "#100", "#102", "1.0", IconResourceID := 400)> _   
    <ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)> _   
    <ProvideMenuResource(1000, 1)> _   
    <ProvideToolboxItemConfigurationAttribute(GetType(ToolboxConfig))> _   
    <GuidAttribute("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Public Class ItemConfiguration   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideToolboxItemsAttribute(3)]  
    [DefaultRegistryRoot("Software\\Microsoft\\VisualStudio\\8.0")]  
    [InstalledProductRegistration(false, "#100", "#102", "1.0", IconResourceID = 400)]  
    [ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)]  
    [ProvideMenuResource(1000, 1)]  
    [ProvideToolboxItemConfigurationAttribute(typeof(ToolboxConfig))]  
  
    [GuidAttribute("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    public class ItemConfiguration : Package  
    ```  
  
## 自訂的拖放支援  
 除了要加入至**工具箱** ， <xref:System.Drawing.Design.ToolboxItem>物件和它們的實作可以用來擴充中的拖放支援[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE。  這可以讓任意的剪貼簿格式，以公開給**工具箱** ，在編輯器中。  
  
 管理套件架構為基礎的 VSPackages 必須登錄為提供自訂**工具箱**項目所套用的執行個體的剪貼簿格式， <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute>類別實作<xref:Microsoft.VisualStudio.Shell.Package>。  
  
 如需詳細資訊，以適當地註冊**工具箱**提供者，請參閱[註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)。  
  
#### 若要提供自訂的剪貼簿格式及拖放支援工具箱控制項  
  
1.  實作建立<xref:System.Drawing.Design.ToolboxItemCreatorCallback>委派。  
  
     這項實作會傳回<xref:System.Drawing.Design.ToolboxItem>支援非標準的剪貼簿格式的物件。  
  
     項目的實作範例的<xref:System.Drawing.Design.ToolboxItemCreatorCallback>委派，請參閱<xref:System.Drawing.Design.ToolboxItem>和<xref:System.Drawing.Design.ToolboxItemCreatorCallback>參考網頁。  
  
2.  進行這項實作的<xref:System.Drawing.Design.ToolboxItemCreatorCallback>委派可以使用[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]**工具箱**的非標準的工具箱，藉由呼叫<xref:System.Drawing.Design.IToolboxService.AddCreator%2A>。  
  
    ```vb#  
    <GuidAttribute("7D91995B-A799-485e-BFC7-C52545DFB5DD")> _   
    <ProvideToolboxFormatAttribute("MyFormat")> _   
    Public Class ItemConfiguration   
        Inherits MSVSIP.Package   
        Public Overloads Overrides Sub Initialize()   
            '"Adding this class as a ToolboxItemCreator");   
            Dim toolbox As IToolboxService = DirectCast(host.GetService(GetType(IToolboxService)), IToolboxService)   
            If toolbox IsNot Nothing Then   
                toolboxCreator = New ToolboxItemCreatorCallback(Me.OnCreateToolboxItem)   
                toolbox.AddCreator(toolboxCreator, "MyFormat", host)   
            End If   
        End Sub   
    End Class  
    ```  
  
    ```c#  
    [GuidAttribute("7D91995B-A799-485e-BFC7-C52545DFB5DD")]  
    [ProvideToolboxFormatAttribute("MyFormat")]  
    public class ItemConfiguration : MSVSIP.Package  
    {  
        public override void Initialize() {   
            /*  
            *  
            */  
            //"Adding this class as a ToolboxItemCreator");  
            IToolboxService toolbox = (IToolboxService)host.GetService(typeof(IToolboxService));  
            if (toolbox != null) {  
                toolboxCreator = new ToolboxItemCreatorCallback(this.OnCreateToolboxItem);  
                toolbox.AddCreator(toolboxCreator, "MyFormat", host);  
            }  
            private ToolboxItem OnCreateToolboxItem(object serializedData, string format) {  
               /*  
                *  
                */  
            }  
        }  
    }  
    ```  
  
### 本章節內容  
 [如何：支援 \[工具箱\] 的拖放功能](../Topic/How%20to:%20Support%20Toolbox%20Drag-and-Drop%20Functionality.md)  
 說明如何在文件檢視實作拖放支援。  
  
 [如何：使用 Interop 組件提供自訂工具箱項目](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)  
 描述 \[加入新的 ActiveX 控制項，並以新的項目[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]**工具箱**。   這些新的項目時，可能可以有標準的剪貼簿格式或 VSPackage 所支援的自訂格式。  
  
 [註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)  
 說明如何註冊為工具箱提供者的 VSPackage。  同時也談論支援，或使用其他 「 工具箱 」 功能。  
  
## 請參閱  
 [擴充工具箱](../misc/extending-the-toolbox.md)   
 [工具箱逐步解說](../misc/toolbox-walkthroughs.md)   
 [註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)   
 [如何：使用 Interop 組件提供自訂工具箱項目](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)   
 [管理工具箱](../misc/managing-the-toolbox.md)   
 [如何：控制工具箱](../Topic/How%20to:%20Control%20the%20Toolbox.md)