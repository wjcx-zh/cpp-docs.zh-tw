---
title: "Visual Studio Interop 組件參數封送處理 | Microsoft Docs"
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
  - "疑難排解 Visual Studio SDK Interop 組件"
  - "Interop 組件, 參數封送處理"
  - "Interop 組件, 疑難排解"
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Visual Studio Interop 組件參數封送處理
VSPackages 是寫成 managed 程式碼可能需要呼叫或由不受管理的 COM 程式碼呼叫。  一般來說，方法引數轉換，或是，自動由封送處理 interop 封送處理器。  不過，有時候引數無法轉換在直接的方式。  在這些情況下，interop 組件的方法原型參數用來比對 COM 的函式參數時，儘可能相近。  如需詳細資訊，請參閱 [Interop 封送處理](../Topic/Interop%20Marshaling.md)。  
  
## 一般建議  
  
##### 請參閱參考文件  
 讀取每一種方法的參考文件是有效的方法，可偵測交互操作性問題。  
  
 每一種方法的參考文件包含三個相關的各節：  
  
-   [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] COM 函式原型。  
  
-   Interop 組件的方法原型。  
  
-   COM 參數和簡短說明每一份。  
  
##### 尋找兩個原型之間的差異  
 大部分的交互操作性問題衍生自特定型別的 COM 介面中定義，以及在相同的型別定義的緣故[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件。  例如，考慮進行傳遞的差異`null`以 \[out\] 參數的值。  您必須尋找兩個原型之間的差異，並考慮其所傳遞之資料的細節。  
  
##### 讀取參數定義  
 讀取參數定義。  COM 是比通用語言執行階段 \(CLR\) 混用不同的型別中的單一參數的資料較不嚴格。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]的 COM 介面完全利用這種彈性。  任何可以傳送，或需要非標準的值或類型的資料，例如指標參數中的常數值的參數應該依實況描述文件中。  
  
### IUnknown 當做型別 void 貴傳遞的物件  
 \[Out\] 參數定義為型別尋找`void **`在 COM 介面，但這些被定義為`[``iid_is``]`在[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件方法原型。  
  
 某些情況下，會產生 COM 介面`IUnknown`物件和 COM 介面再傳遞型別為`void **`。  這些介面就格外重要因為如果變數定義成 \[out\] 在 IDL 中，然後在`IUnknown`物件是參考計數與`AddRef`方法。  如果物件未正確地處理，就會發生記憶體遺漏。  
  
> [!NOTE]
>  `IUnknown`建立的 COM 介面，因此傳回在 \[out\] 變數的物件會造成記憶體流失，如果未明確釋放。  
  
 受管理處理這類物件的方法應該視為<xref:System.IntPtr>為變數的指標， `IUnknown`物件，然後呼叫<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>取得物件的方法。  呼叫端應該再將傳回值轉換為任何型別適合。  當不再需要物件時，呼叫<xref:System.Runtime.InteropServices.Marshal.Release%2A>將其釋放。  
  
 下列是範例的電話<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>方法，並處理`IUnknown`正確的物件：  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  已知下列方法會傳遞`IUnknown`類型的物件指標<xref:System.IntPtr>。  這一節所述，請處理它們。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### \[Out\] 參數的選擇性  
 尋找以 \[out\] 所定義的參數資料型別 \(`int`， `object`，依此類推\) 中的 COM 介面，但這些被定義為在相同的資料型別的陣列[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件方法原型。  
  
 某些 COM 介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，將 \[out\] 參數為選擇項。  如果物件不是必要的這些 COM 介面傳回`null`做為該參數，而不是建立 \[out\] 的物件值的指標。  這是設計上的預期行為。  針對這些介面， `null`指標會假設為 VSPackage，正確行為的一部份，並會傳回任何錯誤。  
  
 因為 CLR 並不允許以 \[out\] 參數的值`null`，原本設計的作法，這些介面的組件不是直接使用 managed 程式碼內。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]受影響的介面的 interop 組件方法能解決問題，只要定義作為陣列的相關參數，因為 CLR 允許經過的`null`陣列。  
  
 受管理的實作，這些方法都應該置於`null`參數時沒有傳回任何項目到陣列。  否則，建立正確型別的單一元素陣列，並將傳回的值放在陣列中。  
  
 管理介面具有選擇性 \[out\] 接收資訊的方法參數接收的參數做為陣列。  只檢查陣列的第一個元素的值。  如果不是`null`，將視為第一個項目因為原始的參數。  
  
### 在 \[指標參數的傳遞常數  
 尋找的參數所定義為 \[in\] 在中的 COM 介面的指標，但定義為<xref:System.IntPtr>中輸入[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件方法原型。  
  
 COM 介面傳遞特殊的值，例如 0、\-1 或 – 2，而非物件指標時，就會發生類似的問題。  不像[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]，CLR 不允許轉換成物件的常數。  相反地， [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件定義的參數做為<xref:System.IntPtr>型別。  
  
 受管理的這些方法的實作應該利用這個事實， <xref:System.IntPtr>類別有兩個`int`和`void *`建構函式來建立<xref:System.IntPtr>從物件或整數格式中，視需要。  
  
 管理接收的方法<xref:System.IntPtr>應該使用這個型別參數的<xref:System.IntPtr>型別轉換運算子來處理結果。  第一次轉換<xref:System.IntPtr>到`int` ，並測試相關的整數常數。  如果沒有值相符，請將它轉換成所需型別的物件，並繼續。  
  
 這個範例，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。  
  
### OLE 傳回值傳遞做為 \[out\] 參數  
 尋找具有方法`retval`在 COM 介面，但具有傳回值`int`傳回值和其他 \[out\] 陣列參數中[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件方法原型。  它也應該很清楚這些方法需要特殊處理，因為[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件方法原型有比 COM 介面方法的多個參數。  
  
 許多 OLE 活動所應付的 COM 介面傳送 OLE 狀態資訊傳回給呼叫程式儲存在`retval`傳回值的介面。  代替使用傳回的值，對應的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件的方法將資訊傳回呼叫程式儲存在 \[out\] 陣列參數。  
  
 受管理的實作，這些方法應建立 \[out\] 參數型別相同的單一元素陣列，並將它放在參數中。  陣列元素的值應該是適當的 COM 一樣`retval`。  
  
 \[Out\] 陣列的第一個元素就會呼叫這個型別的介面的 managed 的方法提取。  可以處理這個項目，就好像`retval`從對應的 COM 介面傳回值。  
  
## 請參閱  
 [Interop Marshaling](http://msdn.microsoft.com/zh-tw/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop 封送處理](../Topic/Interop%20Marshaling.md)   
 [Troubleshooting Interoperability](../Topic/Troubleshooting%20Interoperability%20\(Visual%20Basic\).md)   
 [Managed VSPackage](../misc/managed-vspackages.md)