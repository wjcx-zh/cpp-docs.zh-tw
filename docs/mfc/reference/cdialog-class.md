---
title: "CDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialog class"
  - "MFC 對話方塊, 基底類別"
  - "強制回應對話方塊, 建立"
  - "非強制回應對話方塊, 建立"
  - "非強制回應對話方塊, 顯示"
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定顯示在螢幕上的  對話方塊的基底類別。  
  
## 語法  
  
```  
class CDialog : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDialog::CDialog](../Topic/CDialog::CDialog.md)|建構 `CDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDialog::Create](../Topic/CDialog::Create.md)|初始化 `CDialog` 物件。  建立非強制回應對話方塊並將其附加至 `CDialog` 物件。|  
|[CDialog::CreateIndirect](../Topic/CDialog::CreateIndirect.md)|若要從建立對話方塊樣板的非強制回應對話方塊在記憶體中 \(不是以為基礎的資源\)。|  
|[CDialog::DoModal](../Topic/CDialog::DoModal.md)|呼叫強制回應對話方塊並傳回，完成。|  
|[CDialog::EndDialog](../Topic/CDialog::EndDialog.md)|關閉強制回應對話方塊。|  
|[CDialog::GetDefID](../Topic/CDialog::GetDefID.md)|取得預設按鈕控制項 ID\] 對話方塊中的。|  
|[CDialog::GotoDlgCtrl](../Topic/CDialog::GotoDlgCtrl.md)|將焦點移至  對話方塊中指定的對話方塊控制項。|  
|[CDialog::InitModalIndirect](../Topic/CDialog::InitModalIndirect.md)|若要從建立對話方塊樣板的強制回應對話方塊在記憶體中 \(不是以為基礎的資源\)。  儲存參數，直到 `DoModal` 函式呼叫。|  
|[CDialog::MapDialogRect](../Topic/CDialog::MapDialogRect.md)|轉換矩形的對話方塊單位篩選單位。|  
|[CDialog::NextDlgCtrl](../Topic/CDialog::NextDlgCtrl.md)|將焦點移至  對話方塊中的  對話方塊的控制項。|  
|[CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)|擴大對話方塊初始化的覆寫。|  
|[CDialog::OnSetFont](../Topic/CDialog::OnSetFont.md)|指定字型的覆寫對話方塊控制項是使用時所繪製文字。|  
|[CDialog::PrevDlgCtrl](../Topic/CDialog::PrevDlgCtrl.md)|將焦點移至  對話方塊中的上一個對話方塊控制項。|  
|[CDialog::SetDefID](../Topic/CDialog::SetDefID.md)|若要變更對話方塊的預設按鈕控制項加入至指定的按鈕。|  
|[CDialog::SetHelpID](../Topic/CDialog::SetHelpID.md)|設定對話方塊的即時線上說明 ID。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CDialog::OnCancel](../Topic/CDialog::OnCancel.md)|執行取消按鈕或 ESC 按鍵動作的覆寫。  預設關閉對話方塊並 **DoModal** 傳回 **IDCANCEL**。|  
|[CDialog::OnOK](../Topic/CDialog::OnOK.md)|執行 \[確定\] 按鈕動作的覆寫在強制回應對話方塊。  預設關閉對話方塊並 `DoModal` 傳回 **IDOK**。|  
  
## 備註  
 對話方塊有兩種類型:強制回應 \(Modal\) 和非強制回應。  在中，應用程式會繼續執行之前，必須由使用者關閉強制回應對話方塊。  非強制回應對話方塊能讓使用者顯示對話方塊並回到另一項工作，而不需移除或移除  對話方塊。  
  
 `CDialog` 物件是對話方塊樣板和 `CDialog`衍生類別的組合。  使用對話方塊編輯器建立對話方塊樣板資源以及儲存它，然後使用加入類別精靈會從 `CDialog`衍生自類別的類別。  
  
 顯示對話方塊，如同其他視窗，取得從視窗的訊息。  在  對話方塊中，您會特別為此後的處理對話方塊的控制項傳回的通知訊息所需的使用者如何與您的對話方塊互動。  使用訊息要處理常式，它會將適當的訊息對應 \(Message Map 輸入和訊息處理常式成員函式加入至類別的 \[屬性\] 視窗中選取 。  您在處理常式成員函式只需要撰寫應用程式特定的程式碼。  
  
 如果想要的話，您可以撰寫訊息對應 \(Message Map 輸入，而成員手動地運作。  
  
 除了最普通對話方塊中，您將成員變數加入至衍生自類別的對話方塊類別加入至對話方塊的控制項中輸入的資料存放區由使用者或為使用者顯示資料。  您可以使用加入變數精靈來建立成員變數並與控制項。  同時，您選取值的變數的型別和允許的範圍內的每個變數的。  程式碼精靈加入成員變數加入至衍生自類別的對話方塊類別。  
  
 資料將會自動處理資料交換在成員變數和對話方塊的控制項。  資料將提供使用  對話方塊中的控制項具有適當的值，擷取資料，並驗證資料的函式。  
  
 若要建立強制回應對話方塊，請建構在堆疊上的物件使用所衍生的對話方塊類別的建構函式來建立 `DoModal` 對話視窗和它的控制項。  如果您想要建立非強制回應對話方塊，請在您的對話方塊類別建構函式的呼叫 **建立** 。  
  
 您也可以在記憶體中建立一個範本使用 [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) 資料結構 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]\(如中所述。  在建構 `CDialog` 物件後，請呼叫 [CreateIndirect](../Topic/CDialog::CreateIndirect.md) 建立非強制回應對話方塊或呼叫 [InitModalIndirect](../Topic/CDialog::InitModalIndirect.md) 和 [DoModal](../Topic/CDialog::DoModal.md) 建立強制回應對話方塊。  
  
 交換和驗證資料將加入到新的對話方塊類別 `CWnd::DoDataExchange` 的覆寫中。  如需更多參閱 [DoDataExchange](../Topic/CWnd::DoDataExchange.md) 成員函式在 `CWnd` 在交換和驗證功能。  
  
 這個程式設計人員和架構藉由呼叫方法間接呼叫 `DoDataExchange` 至 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)。  
  
 當使用者按一下 \[確定\] 按鈕關閉強制回應對話方塊時，架構會呼叫 `UpdateData` 。  \(資料不會擷取，如果取消按鈕按一下 \)。[OnInitDialog](../Topic/CDialog::OnInitDialog.md) 的預設實作會呼叫 `UpdateData` 設定控制項的初始值。  通常您會覆寫 `OnInitDialog` 進一步初始化控制項。  `OnInitDialog` 呼叫，在所有對話方塊控制項，並建立之後，在  對話方塊中顯示之前。  
  
 您可以在強制回應或非強制回應對話方塊執行期間隨時呼叫 `CWnd::UpdateData` 。  
  
 如果您以手動方式開發與  對話方塊中，您將需要的成員變數加入至衍生自類別的對話方塊類別，然後，您將成員函式設定或取得這些值。  
  
 強制回應對話方塊自動關閉，當使用者按下 \[確定\] 或 \[取消\] 按鈕時，或當您的程式碼呼叫 `EndDialog` 成員函式時。  
  
 當您實作非強制回應對話方塊時，請務必覆寫 `OnCancel` 成員函式和呼叫 `DestroyWindow` 從其內部。  不要呼叫基底類別 `CDialog::OnCancel`，，因為它會呼叫 `EndDialog`，讓對話方塊不可見，但不會終結它。  因為非強制回應對話方塊通常會以 **new**，則也應覆寫和非強制回應對話方塊的 `PostNcDestroy` 才能移除 **this**。  強制回應對話方塊顯示在框架通常會建構，並不需要 `PostNcDestroy` 清除。  
  
 如需 `CDialog`的資訊，請參閱:  
  
-   [對話方塊](../../mfc/dialog-boxes.md)  
  
-   知識庫文件 Q262954:HOWTO:建立具有捲軸的 Resizeable 對話方塊  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 DLG CBR32](../../top/visual-cpp-samples.md)   
 [MFC 範例 DLGTEMPL](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)