---
title: "MFC ActiveX 控制項：當地語系化 ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LocaleID"
  - "AfxOleRegisterTypeLib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LocaleID 環境屬性"
  - "當地語系化, ActiveX 控制項"
  - "LOCALIZE 範例 [MFC]"
  - "MFC ActiveX 控制項, 當地語系化"
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：當地語系化 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論當地語系化 ActiveX 控制項介面的方法。  
  
 如果您要將 ActiveX 控制項移植到國際化市場，您可能要當地語系化控制項。  除了預設英文以外，包括德文、法文和瑞典文，Windows 支援許多語言。  如果它的介面只用英文，這可能造成控制項的問題。  
  
 一般而言， ActiveX 控制項應該永遠根據使用者的地區設定環境 LocaleID 屬性。  執行這項作業的方法有三種：  
  
-   載入資源，一定在需要時，根據環境 LocaleID 屬性的目前值。  MFC ActiveX 控制項範例 [當地語系化](../top/visual-cpp-samples.md) 使用這項策略。  
  
-   如果第一個控制項根據環境 LocaleID 屬性成為執行個體時就載入資源，以及為其他執行個體使用這些資源。  本文件示範這個策略。  
  
    > [!NOTE]
    >  如果未來的執行個體有不同的地區設定，在一些情況下無法正常運作。  
  
-   使用 **OnAmbientChanged** 告知函式為容器的地區設定動態載入適當資源。  
  
    > [!NOTE]
    >  這在控制項中能夠運作，不過，當環境 LocaleID 屬性變更時執行階段 DLL 不會動態更新其資源。  此外，ActiveX 控制項的執行階段 DLL 使用執行緒地區設定決定其資源的地區設定。  
  
 本文的其餘說明兩個當地語系化的策略。  第一項策略 [當地語系化控制項的可程式性介面](#_core_localizing_your_control.92.s_programmability_interface) \(屬性、方法和事件名稱\)。  第二個策略， [當地語系化控制項的使用者介面](#_core_localizing_the_control.92.s_user_interface) 使用容器的環境 LocaleID 屬性。  如需控制項當地語系化的示範，請參閱 MFC ActiveX 控制項範例 [當地語系化](../top/visual-cpp-samples.md)。  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> 當地語系化控制項的可程式性介面  
 在當地語系化控制項的可程式性介面 \(程式設計人員使用的介面將使用您的控制項\) 的應用程式時，您必須為每種要支援的語言建立控制 .IDL 檔案 \(建立的控制項型別程式庫\) 執行指令碼的修改版本。  這是您需要當地語系化控制項屬性名稱的唯一欄位。  
  
 當您開發定位控制項時，在這個型別程式庫等級包含地區設定 ID 做為屬性。  例如，如果您要提供法語的當地語系化屬性名稱的型別程式庫，請拷貝您的 SAMPLE.IDL 檔案，並命名為 SAMPLEFR.IDL。  加入地區設定 ID 屬性至檔案 \(法文的地區設定 ID 是 0x040c\)，如下所示:  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 於 SAMPLEFR.IDL 變更屬性名稱至對等的法文，然後使用 MKTYPLIB.EXE 產生法國型別程式庫， SAMPLEFR.TLB。  
  
 若要建立多個當地語系化型別程式庫，您可以將任何當地語系化 .IDL 檔案加入至專案，然後它們會自動建立。  
  
#### 若要將 .IDL 檔加入至您的 ActiveX 控制項專案  
  
1.  開啟控制項的專案，在 **Project** 功能表上，按一下 \[**加入現有項目**\]。  
  
     \[**加入現有項目**\] 對話方塊隨即出現。  
  
2.  如果需要，請選取磁碟機和目錄檢視。  
  
3.  在 \[檔案類型\] 方塊裡，選擇 \[**所有檔案 \(\*.\*\)**\]。  
  
4.  在檔案清單方塊中，按兩下您想要插入至專案的 .IDL 檔案。  
  
5.  當您已加入所有必要的 .IDL 檔案時，請按一下 **Open** 。  
  
 由於檔案加入至專案，當專案的其他部分建立時，才會建立它們。  當地語系化型別程式庫位於目前 ActiveX 控制項專案目錄。  
  
 在程式碼中，永遠使用內部屬性名稱 \(通常以英文\) 且從未當地語系化。  這包括控制項分派對應，屬性切換函式和您的屬性頁資料交換的程式碼。  
  
 只有一個型別程式庫 \(.TLB\) 檔可繫結至控制項實作 \(.OCX\) 檔案中的資源。  這通常是標準化 \(通常是英文\) 名稱的版本。  傳輸需要傳輸 .OCX \(已繫結至預設 .TLB 版本\) 控制項的當地語系化版本和適當地區設定的 .TLB。  這表示只有英文版本 .OCX 需要，因為正確的 .TLB 已繫結至它。  對於其他地區設定，當地語系化型別程式庫也必須與 .OCX 傳輸。  
  
 為了確保您的控制項的用戶端可以找到當地語系化型別程式庫，請註冊您的地區設定特性 .TLB 檔在 Windows 系統註冊的 TypeLib 區段下。  為了這個目的而提供這個 [AfxOleRegisterTypeLib](../Topic/AfxOleRegisterTypeLib.md) 函式的第三個參數 \(通常是選擇性\) 。  下列範例會註冊 ActiveX 控制項的法文型別程式庫:  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 當控制項已註冊，則 `AfxOleRegisterTypeLib` 函式會自動在相同資料夾以控制項尋找指定的 .TLB 檔並註冊在 Windows 系統註冊資料庫。  如果 .TLB 檔案找不到，函式不會有任何作用。  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> 當地語系化控制項的使用者介面  
 若要當地語系化控制項的使用者介面，將所有控制項的使用者可見的資源 \(例如屬性頁和錯誤訊息\) 至語言特定的資源 DLL。  然後您可以使用容器的環境 LocaleID 屬性為使用者地區設定選取適當的 DLL。  
  
 下列程式碼範例將示範一種方法來尋找和載入特定地區設定的資源 DLL。  這個成員函式，為這個範例呼叫 `GetLocalizedResourceHandle` ，可以是您的 ActiveX 控制項類別的成員函式:  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 請注意副語言 ID 可能在 switch 陳述式中的每一種情況下檢查，提供特殊當地語系化。  如需這個函式的示範，請參閱 MFC ActiveX 控制項範例 [當地語系化](../top/visual-cpp-samples.md)的 `GetResourceHandle` 函式。  
  
 當控制項第一次載入自己進入容器時，它會呼叫 [COleControl::AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md) 擷取地區設定 ID。  控制項可以傳遞傳回的地區設定 ID 值到 `GetLocalizedResourceHandle` 函式，這載入適當的資源程式庫。  控制項應該傳遞產生的控制代碼，如果有的話，加入至 [AfxSetResourceHandle](../Topic/AfxSetResourceHandle.md):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 將上述程式碼範例至入控制項的成員函式，例如 [COleControl::OnSetClientSite](../Topic/COleControl::OnSetClientSite.md)覆寫。  此外， `m_hResDLL` 應該是控制項類別的成員變數。  
  
 您可以使用類似的邏輯當地語系化控制項的屬性頁。  若要當地語系化屬性頁，請加入將類似下列範例的程式碼至屬性頁的實作檔 \(在 [COlePropertyPage::OnSetPageSite](../Topic/COlePropertyPage::OnSetPageSite.md)覆寫\):  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)