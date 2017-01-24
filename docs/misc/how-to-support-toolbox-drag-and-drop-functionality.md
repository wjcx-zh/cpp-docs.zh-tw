---
title: "如何：支援 [工具箱] 的拖放功能 | Microsoft Docs"
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
  - "拖放, [工具箱] 支援"
  - "工具箱 [Visual Studio SDK], 用戶端"
  - "工具箱 [Visual Studio SDK], 拖放"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# 如何：支援 [工具箱] 的拖放功能
> [!NOTE]
>  在 \[工具箱\] 加入自訂控制項的建議方式是使用隨附於 Visual Studio 10 SDK，包含拖放支援的 \[工具箱控制項\] 範本。 本主題僅為回溯相容性及處理現有控制項之目的而保留。  
>   
>  如需使用範本建立 \[工具箱\] 控制項的詳細資訊，請參閱[如何：建立使用 Windows Forms 的 \[工具箱\] 控制項](../Topic/How%20to:%20Create%20a%20Toolbox%20Control%20That%20Uses%20Windows%20Forms.md) 和 [建立 WPF 工具箱控制項](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)。  
  
 如果 VSPackages 要在文件檢視上使用 \[工具箱\] 控制項，例如編輯器或設計工具，即必須實作拖放支援。  
  
 根據預設，所有衍生自 <xref:System.Windows.Forms.Control?displayProperty=fullName> 的 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 物件都會自動明確地支援 \[工具箱\] 控制項的使用，所以不需要下文描述的程序。 建立設計工具可以擴充基本功能。  
  
 如需詳細資訊，請參閱 [Windows Form 概觀](../Topic/Windows%20Forms%20Overview.md) 與 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)。  
  
### 實作基本的拖放功能  
  
1.  在檢視物件上實作 <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> 可以提供拖放支援。 這會提供具有 OLE 拖放功能和控制項序列化的檢視。  
  
     如需實作拖放功能的詳細資訊，請參閱[拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)。  
  
     置放的物件可以是剪貼簿項目或置放在設計工具上的控制項。 如需 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \[工具箱\] 支援的標準剪貼簿格式相關資訊，請參閱[擴充工具箱](../misc/extending-the-toolbox.md)。  
  
2.  提供文件檢視的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 介面基本實作。  
  
     當使用者嘗試將 \[工具箱\] 控制項拖曳到檢視中時，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 殼層會查詢檢視的 VSPackage 是否實作了 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 介面。  
  
    1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>，為置放標的支援的那些 \[工具箱\] 格式傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。 下例會查看資料物件是否為自訂剪貼簿格式 \(`CF_CUSTOM_FORMAT`\) 以及物件是否為 ActiveX 控制項。  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         IDE 會在檢視視窗第一次載入時檢查這項資訊，而且檢視視窗每次啟動，使用者都會透過 IDE 的 \[自訂\]、\[工具箱\] 對話方塊，重設 \[工具箱\]。 \[工具箱\] 一般不會顯示不支援的 \[工具箱\] 項目。  
  
         使用者可以設定選項，隨時顯示 \[工具箱\] 的所有頁面。 如此，環境不會查詢編輯器是否有 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>。  
  
    2.  在 <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> 實作 \(如上述那一個\) 成功處理置放的元件之後，檢視物件必須呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A>，將此情況通知 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 環境。  
  
     如有需要，VSPackage 可藉由擴充其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 實作以擴充其拖放支援。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 實作可以選取的方式，而不是滑鼠動作，支援將 \[工具箱\] 項目拖曳至視窗中。 也就是在使用者按兩下 \[工具箱\] 項目，或在按一下後按下 ENTER 鍵時拖曳項目。 做法：  
  
    1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> 方法。  
  
         IDE 呼叫的這個方法，是透過按一下或按下 ENTER 鍵所選取。  
  
         方法應該將 \[工具箱\] 項目插入目標視窗中。  
  
    2.  如果不想透過選取支援實作，這個方法應傳回 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>。  
  
         在下例中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> 方法的實作會檢查是否支援選取的物件，如果支援，則將它還原序列化成程式碼：  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  執行下列步驟，以確保維護應用程式的適當重點：  
  
    1.  如果編輯器視窗實作的是兩個不同的窗格，而不是兩種不同的檢視，請在編輯器視窗中切換窗格啟動時，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A> 方法。 只有您知道視窗內何時會發生啟動變更。  
  
    2.  若要正常啟動視窗並確保正確更新命令路由，您必須對元件呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 方法。 當您設定與 \[工具箱\] 有關的拖放作業所建立或修改的元件視窗焦點時，如編輯器，必須採取此動作。  
  
 VSPackage 可能需要透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> 介面介入拖曳作業及修改已置放項目。  
  
 例如，VSPackage 不會明確地將新的 \[工具箱\] 控制項加入 \[工具箱\]， 而是可能會在置放標準的 \[工具箱\] 時攔截它，並用自訂的實作取而代之。  
  
### 動態修改 \[工具箱\] 控制項  
  
1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> 方法。  
  
     每當選取或置放 \[工具箱\] 項目時，\[工具箱\] 都會查詢置放標的，查看它是否支援 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> 介面，以及它是否真的呼叫了 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> 方法。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> 方法必須傳回要使用的新 <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> 物件，不是傳回原本的 <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject>。  
  
     如果置放標的不需要覆寫資料物件，應該要傳回其輸入。  
  
 VSPackage 可以允許使用者按下 CTRL\+SHIFT\+V 以循環剪貼簿的內容。  
  
### 支援剪貼環  
  
1.  實作 `CMDIDPasteNextTBXCBItem` 命令的處理常式，使用：  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>，適用於 Interop 組件架構的 Vspackage。  
  
    -   <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>，適用於 Managed Package Framework 架構的 VSPackage。<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler> 介面。  
  
2.  在命令處理常式中實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A> 方法，判斷是否有任何循環的剪貼簿物件。  
  
    1.  如果 \[工具箱\] 剪貼簿上沒有任何項目，環境會檢查系統的剪貼簿是否有任何項目。  
  
    2.  如果系統剪貼簿上有項目，但 \[工具箱\] 剪貼簿上沒有項目，剪貼環就會填入系統項目。  
  
    3.  若要選取清單上的下一個項目，實作應呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A> 方法。  
  
    4.  若要返回剪貼簿週期的開頭，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A> 方法。  
  
## 請參閱  
 [擴充工具箱](../misc/extending-the-toolbox.md)   
 [如何：使用 Interop 組件提供自訂工具箱項目](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)   
 [進階工具箱控制項開發](../misc/advanced-toolbox-control-development.md)   
 [註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)   
 [管理工具箱](../misc/managing-the-toolbox.md)