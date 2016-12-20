---
title: "CTaskDialog Class | Microsoft Docs"
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
  - "CTaskDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTaskDialog class"
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTaskDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的運作方式訊息方塊，但的快顯對話方塊可以顯示其他資訊給使用者。  `CTaskDialog` 也包含收集的資訊功能從使用者。  
  
## 語法  
  
```  
class CTaskDialog : public CObject  
```  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[CTaskDialog::CTaskDialog](../Topic/CTaskDialog::CTaskDialog.md)|建構 `CTaskDialog` 物件。|  
  
### 方法  
  
|||  
|-|-|  
|[CTaskDialog::AddCommandControl](../Topic/CTaskDialog::AddCommandControl.md)|將命令按鈕控制項加入至 `CTaskDialog`。|  
|[CTaskDialog::AddRadioButton](../Topic/CTaskDialog::AddRadioButton.md)|將選項按鈕加入至 `CTaskDialog`。|  
|[CTaskDialog::ClickCommandControl](../Topic/CTaskDialog::ClickCommandControl.md)|按一下  命令按鈕控制項或一般按鈕以程式設計的方式設定屬性。|  
|[CTaskDialog::ClickRadioButton](../Topic/CTaskDialog::ClickRadioButton.md)|按一下  選項按鈕的方式。|  
|[CTaskDialog::DoModal](../Topic/CTaskDialog::DoModal.md)|顯示`CTaskDialog`。|  
|[CTaskDialog::GetCommonButtonCount](../Topic/CTaskDialog::GetCommonButtonCount.md)|擷取可用常用的按鈕數目。|  
|[CTaskDialog::GetCommonButtonFlag](../Topic/CTaskDialog::GetCommonButtonFlag.md)|轉換標準 Windows 按鈕通用按鈕類型與 `CTaskDialog` 類別。|  
|[CTaskDialog::GetCommonButtonId](../Topic/CTaskDialog::GetCommonButtonId.md)|一般按鈕類型的轉換無法對應與 `CTaskDialog` 類別至標準 Windows 按鈕。|  
|[CTaskDialog::GetOptions](../Topic/CTaskDialog::GetOptions.md)|傳回這 `CTaskDialog`的選項旗標。|  
|[CTaskDialog::GetSelectedCommandControlID](../Topic/CTaskDialog::GetSelectedCommandControlID.md)|傳回所選取命令的按鈕控制項。|  
|[CTaskDialog::GetSelectedRadioButtonID](../Topic/CTaskDialog::GetSelectedRadioButtonID.md)|傳回所選取的選項按鈕。|  
|[CTaskDialog::GetVerificationCheckboxState](../Topic/CTaskDialog::GetVerificationCheckboxState.md)|擷取驗證核取方塊的狀態。|  
|[CTaskDialog::IsCommandControlEnabled](../Topic/CTaskDialog::IsCommandControlEnabled.md)|決定命令按鈕控制項或一般按鈕是否已啟用。|  
|[CTaskDialog::IsRadioButtonEnabled](../Topic/CTaskDialog::IsRadioButtonEnabled.md)|判斷選項按鈕是否已啟用。|  
|[CTaskDialog::IsSupported](../Topic/CTaskDialog::IsSupported.md)|判斷執行應用程式的電腦是否支援 `CTaskDialog`。|  
|[CTaskDialog::LoadCommandControls](../Topic/CTaskDialog::LoadCommandControls.md)|若要將命令按鈕控制項會使用資料來自字串資料表。|  
|[CTaskDialog::LoadRadioButtons](../Topic/CTaskDialog::LoadRadioButtons.md)|將選項按鈕使用資料來自字串資料表。|  
|[CTaskDialog::NavigateTo](../Topic/CTaskDialog::NavigateTo.md)|會將焦點傳送至另一個 `CTaskDialog`。|  
|[CTaskDialog::OnCommandControlClick](../Topic/CTaskDialog::OnCommandControlClick.md)|當使用者按一下命令按鈕控制項時，架構會呼叫這個方法。|  
|[CTaskDialog::OnCreate](../Topic/CTaskDialog::OnCreate.md)|在建立 `CTaskDialog`之後，架構會呼叫這個方法。|  
|[CTaskDialog::OnDestroy](../Topic/CTaskDialog::OnDestroy.md)|其 `CTaskDialog`終結之前，架構會呼叫這個方法。|  
|[CTaskDialog::OnExpandButtonClick](../Topic/CTaskDialog::OnExpandButtonClick.md)|當使用者按一下展開按鈕時，架構會呼叫這個方法。|  
|[CTaskDialog::OnHelp](../Topic/CTaskDialog::OnHelp.md)|以使用者要求說明時，架構會呼叫這個方法。|  
|[CTaskDialog::OnHyperlinkClick](../Topic/CTaskDialog::OnHyperlinkClick.md)|當使用者按一下超連結時，架構會呼叫這個方法。|  
|[CTaskDialog::OnInit](../Topic/CTaskDialog::OnInit.md)|當 `CTaskDialog` 初始化時，架構會呼叫這個方法。|  
|[CTaskDialog::OnNavigatePage](../Topic/CTaskDialog::OnNavigatePage.md)|當使用者將焦點有關在 `CTaskDialog`控制項時，架構會呼叫這個方法。|  
|[CTaskDialog::OnRadioButtonClick](../Topic/CTaskDialog::OnRadioButtonClick.md)|在使用者選取選項按鈕控制項時，架構會呼叫這個方法。|  
|[CTaskDialog::OnTimer](../Topic/CTaskDialog::OnTimer.md)|當計時器過期時，架構會呼叫這個方法。|  
|[CTaskDialog::OnVerificationCheckboxClick](../Topic/CTaskDialog::OnVerificationCheckboxClick.md)|當使用者按一下驗證核取方塊時，架構會呼叫這個方法。|  
|[CTaskDialog::RemoveAllCommandControls](../Topic/CTaskDialog::RemoveAllCommandControls.md)|從移除所有 `CTaskDialog`排列控制項。|  
|[CTaskDialog::RemoveAllRadioButtons](../Topic/CTaskDialog::RemoveAllRadioButtons.md)|從 `CTaskDialog`移除所有選項按鈕。|  
|[CTaskDialog::SetCommandControlOptions](../Topic/CTaskDialog::SetCommandControlOptions.md)|更新在 `CTaskDialog`的命令按鈕控制項。|  
|[CTaskDialog::SetCommonButtonOptions](../Topic/CTaskDialog::SetCommonButtonOptions.md)|更新會啟用一般按鈕的子集 UAC 需要提高權限。|  
|[CTaskDialog::SetCommonButtons](../Topic/CTaskDialog::SetCommonButtons.md)|將一般的按鈕加入至 `CTaskDialog`。|  
|[CTaskDialog::SetContent](../Topic/CTaskDialog::SetContent.md)|`CTaskDialog`更新的內容。|  
|[CTaskDialog::SetDefaultCommandControl](../Topic/CTaskDialog::SetDefaultCommandControl.md)|指定預設命令按鈕控制項。|  
|[CTaskDialog::SetDefaultRadioButton](../Topic/CTaskDialog::SetDefaultRadioButton.md)|指定預設選項按鈕。|  
|[CTaskDialog::SetDialogWidth](../Topic/CTaskDialog::SetDialogWidth.md)|調整 `CTaskDialog`的寬度。|  
|[CTaskDialog::SetExpansionArea](../Topic/CTaskDialog::SetExpansionArea.md)|更新 `CTaskDialog`展開的區域。|  
|[CTaskDialog::SetFooterIcon](../Topic/CTaskDialog::SetFooterIcon.md)|更新 `CTaskDialog`尾圖示。|  
|[CTaskDialog::SetFooterText](../Topic/CTaskDialog::SetFooterText.md)|更新在 `CTaskDialog`的頁尾文字。|  
|[CTaskDialog::SetMainIcon](../Topic/CTaskDialog::SetMainIcon.md)|更新 `CTaskDialog`的主要圖示。|  
|[CTaskDialog::SetMainInstruction](../Topic/CTaskDialog::SetMainInstruction.md)|更新 `CTaskDialog`主要的指示。|  
|[CTaskDialog::SetOptions](../Topic/CTaskDialog::SetOptions.md)|設定 `CTaskDialog`的選項。|  
|[CTaskDialog::SetProgressBarMarquee](../Topic/CTaskDialog::SetProgressBarMarquee.md)|設定 `CTaskDialog` 之跑馬燈並將其加入至  對話方塊。|  
|[CTaskDialog::SetProgressBarPosition](../Topic/CTaskDialog::SetProgressBarPosition.md)|調整進度列的位置。|  
|[CTaskDialog::SetProgressBarRange](../Topic/CTaskDialog::SetProgressBarRange.md)|調整進度列的範圍。|  
|[CTaskDialog::SetProgressBarState](../Topic/CTaskDialog::SetProgressBarState.md)|設定進度列的狀態並將它顯示在 `CTaskDialog`。|  
|[CTaskDialog::SetRadioButtonOptions](../Topic/CTaskDialog::SetRadioButtonOptions.md)|啟用或停用選項按鈕。|  
|[CTaskDialog::SetVerificationCheckbox](../Topic/CTaskDialog::SetVerificationCheckbox.md)|設定驗證核取方塊的選取狀態。|  
|[CTaskDialog::SetVerificationCheckboxText](../Topic/CTaskDialog::SetVerificationCheckboxText.md)|在驗證核取方塊的右邊設定文字。|  
|[CTaskDialog::SetWindowTitle](../Topic/CTaskDialog::SetWindowTitle.md)|設定 `CTaskDialog`的標題。|  
|[CTaskDialog::ShowDialog](../Topic/CTaskDialog::ShowDialog.md)|建立和顯示 `CTaskDialog`。|  
|[CTaskDialog::TaskDialogCallback](../Topic/CTaskDialog::TaskDialogCallback.md)|架構會呼叫這個回應各種 Windows 訊息。|  
  
### 資料成員  
  
|||  
|-|-|  
|`m_aButtons`|陣列 `CTaskDialog`的命令按鈕控制項。|  
|`m_aRadioButtons`|`CTaskDialog`的選項按鈕控制項。|  
|`m_bVerified`|`TRUE` 表示驗證核取方塊被選取， `FALSE` 表示未啟用。|  
|`m_footerIcon`|在 `CTaskDialog`的頁尾的圖示。|  
|`m_hWnd`|的控制代碼 `CTaskDialog`的視窗。|  
|`m_mainIcon`|`CTaskDialog`的主要圖示。|  
|`m_nButtonDisabled`|表示遮罩的一般按鈕已停用。|  
|`m_nButtonElevation`|表示遮罩的一般按鈕 UAC 要求提高權限。|  
|`m_nButtonId`|將選取的命令按鈕控制項的 ID。|  
|`m_nCommonButton`|表示遮罩的一般按鈕在 `CTaskDialog`隨即顯示。|  
|`m_nDefaultCommandControl`|選取命令按鈕控制項的 ID，當 `CTaskDialog` 隨即顯示。|  
|`m_nDefaultRadioButton`|選取選項按鈕控制項的 ID，當 `CTaskDialog` 隨即顯示。|  
|`m_nFlags`|表示 `CTaskDialog`選項的遮罩。|  
|`m_nProgressPos`|進度列的目前位置。  這個值必須介於 `m_nProgressRangeMin` 和 `m_nProgressRangeMax` 之間。|  
|`m_nProgressRangeMax`|進度列的最大值。|  
|`m_nProgressRangeMin`|進度列的最小值。|  
|`m_nProgressState`|進度列的狀態。  如需詳細資訊，請參閱 [CTaskDialog::SetProgressBarState](../Topic/CTaskDialog::SetProgressBarState.md)。|  
|`m_nRadioId`|選項按鈕控制項的 ID。|  
|`m_nWidth`|`CTaskDialog` 的寬度 \(以像素為單位\)。|  
|`m_strCollapse`|在 `CTaskDialog` 展開方塊右側顯示的字串，在展開隱藏的資訊。|  
|`m_strContent`|`CTaskDialog`內容的字串。|  
|`m_strExpand`|在 `CTaskDialog` 展開方塊右側顯示的字串，在展開的相關資訊隨即顯示。|  
|`m_strFooter`|`CTaskDialog`的頁尾。|  
|`m_strInformation`|`CTaskDialog`的展開的資訊。|  
|`m_strMainInstruction`|`CTaskDialog`主要的指示。|  
|`m_strTitle`|`CTaskDialog` 的標題。|  
|`m_strVerification`|在 `CTaskDialog` 驗證核取方塊的右邊顯示的字串。|  
  
## 備註  
 `CTaskDialog` 類別取代標準的 Windows 訊息方塊並具有其他功能 \(例如向使用者收集資訊的新控制項。  這個類別會在 [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]的 MFC 程式庫。  `CTaskDialog` 可用開始 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  舊版 Windows 無法顯示 `CTaskDialog` 物件。  使用 `CTaskDialog::IsSupported` 在執行階段判斷目前使用者是否可以顯示工作對話方塊。  標準 Windows 訊息方塊中 [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]仍支援。  
  
 您可以使用 Unicode 程式庫時，，，只有當您建置應用程式 `CTaskDialog` 可用。  
  
 `CTaskDialog` 有兩個不同的建構函式。  建構函式可讓您指定兩個命令按鈕和最多六個標準按鈕控制項。  在建立 `CTaskDialog`之後，您可以將多個命令按鈕。  第二個建構函式不支援任何命令按鈕，不過，您可以加入不限數目的標準按鈕控制項。  如需建構函式的詳細資訊，請參閱 [CTaskDialog::CTaskDialog](../Topic/CTaskDialog::CTaskDialog.md)。  
  
 下圖示範一個範例 `CTaskDialog` 說明一些控制項的位置。  
  
 ![CTaskDialog 範例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialogSample")  
CTaskDialog 範例  
  
## 需求  
 **最小必要的作業系統:** [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
 **標題:** afxtaskdialog.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [逐步解說：將 CTaskDialog 加入至應用程式](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)