---
title: "建立使用 Remote Automation 的程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Remote Automation, 建立程式"
ms.assetid: 8eb31320-1037-4029-b1f3-fdc9406dbaf1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 建立使用 Remote Automation 的程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不需要重新編譯，就不需要重新連結，需要的所有 Automation 物件和任何自動化測試，可以使用 Remote Automation 不做任何變更原始程式碼。  一旦您有本機工作上設定 \(也就是在相同的電腦\)，您需要經過少數步驟遠端執行它。  
  
#### 執行遠端 Automation 物件  
  
1.  登錄記錄在用戶端或電腦的應用程式。  
  
2.  設定用戶端存取使用遠端伺服器。  
  
3.  安裝並註冊在伺服器電腦或電腦的應用程式。  
  
4.  將伺服器設定為允許遠端啟動過程。  
  
5.  安裝伺服器電腦的 Automation 管理員。  
  
6.  在伺服器上的 Automation 管理員。  
  
7.  在用戶端的應用程式。  
  
 步驟 1 透過載入和執行伺服器應用程式最容易在中完成在用戶端，，因為大部分伺服器是自我登錄。  如果您先在本機測試了這個設定，階段已完成。  如果伺服器應用程式不是註冊的自我，您可能想要這樣做它。  否則，您必須提供本機使用者可以執行這個步驟的登錄檔案。  如果您未執行這些作業，您或系統管理員必須手動編輯登錄，因任何建議的程序，除了最進階使用者。  
  
 第 2 步驟是使用遠端自動化連接 \(RAC\) 管理員。  執行 RAC 管理員並確定伺服器連接選項最高。  接著，探索伺服器物件的項目在 **OLE Classes** 窗格並按一下它。  然後移至 **Network Address** 下拉式方塊並輸入遠端可執行檔將會執行伺服器電腦的名稱。  例如，您可以輸入\\ \\ MyServer 這裡。  然後從提供的清單中選擇適當的網路通訊協定。  您可能需要詢問您的網路系統管理員判斷建議使用的通訊協定。  在大部分情況下，這會是 TCP\/IP。  最後，您可以選取驗證層級。  在大部分情況下，這會向左 \(無\) 或預設值。  現在請以滑鼠右鍵按一下 **OLE Classes** 窗格的伺服器。  這可讓您可以選擇本機或遠端作業的捷徑功能表。  選取遠端。  
  
 步驟 3 會正確安裝和註冊在選取的伺服器電腦或電腦的伺服器應用程式。  同樣地，因此，如果應用程式是註冊的自我，執行它也一次註冊它。  
  
 第 4 步驟是將伺服器設定為允許遠端執行。  執行伺服器電腦的 RAC 管理員，並確定 **Client Access** 選項有焦點。  選取您想要的啟動過程模型 \(通常 **Allow Remote Creates by Key**。  如果您選取這個選項，您可能需要按一下 **Allow Remote Activation** 核取方塊設定登錄項目的值為「Y」\)。  如果您執行的是 Windows NT 或 Windows 2000 和您選取允許遠端建立 \(ACL\) 選項，您也可以選擇傳入 **Edit ACL** 按鈕編輯 ACL。  
  
 若要允許遠端自動化運作，您就必須確保自動化管理員已安裝且在伺服器電腦或電腦。  如果尚未安裝，請複製 AUTMGR32.EXE 對 Windows 系統目錄。  如需如何執行的詳細資訊，請參閱 [遠端自動化安裝](../mfc/remote-automation-installation.md)。  若要啟動遠端自動化，執行自動化管理員。  它會顯示一些訊息中顯示的小型狀態視窗。  一旦啟動，它將最小化。  如果您想要繼續檢視狀態資訊，您可以按一下工作列的 **Automation Manager** 選項還原視窗。  
  
 最後一個步驟將在用戶端的用戶端應用程式。  如果您遵循上述步驟，它應該連接到伺服器物件和精確地執行，它時，雖然較慢的點。  
  
 請注意 RAC 管理員也讓您在遠端自動化之間和分散式 COM \(DCOM，在支援 DCOM\) 的平台與選項按鈕的按一下。  如果您選擇 DCOM，您可以將各種配置選項。  如需更多細節，請參閱 DCOM 文件。  
  
## 請參閱  
 [Remote Automation](../mfc/remote-automation.md)   
 [使用 AUTOCLIK 和 AUTODRIV 執行 Remote Automation](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)