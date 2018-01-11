---
title: "建立使用 Remote Automation 的程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, creating programs
ms.assetid: 8eb31320-1037-4029-b1f3-fdc9406dbaf1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: deb832e0baed30507ef3f9929fb5f12805b7a807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-programs-that-use-remote-automation"></a>建立使用 Remote Automation 的程式
不需要變更原始程式碼、不需要重新編譯，也不需要重新連結，任何的 Automation 物件和任何 Automation 控制器，都可以使用 Remote Automation。 一旦有在本機設定工作 (也就是在相同的電腦)，您只需用幾個步驟就能遠端執行。  
  
#### <a name="to-execute-the-remote-automation-object"></a>執行 Remote Automation 物件  
  
1.  在用戶端電腦或電腦上註冊應用程式。  
  
2.  設定用戶端存取以使用遠端伺服器。  
  
3.  在伺服器電腦或電腦上安裝並註冊應用程式。  
  
4.  將伺服器設定為允許遠端啟用。  
  
5.  在伺服器電腦上安裝 Automation 管理員。  
  
6.  在伺服器上執行 Automation 管理員。  
  
7.  在用戶端執行應用程式。  
  
 步驟 1 透過在用戶端電腦載入和執行伺服器應用程式，是最容易完成的，因為大部分伺服器會自我登錄。 如果您先在本機測試這個設定，此階段便已完成。 如果伺服器應用程式未自我登錄，您可能需要讓伺服器應用程式自我登錄。 否則，您必須提供登錄檔案讓本機使用者可以執行這個步驟。 如果您未執行這些作業，您或系統管理員必須手動編輯登錄，這個建議的程序不是針對所有使用者，除了最進階使用者以外。  
  
 第 2 步驟是使用 Remote Automation Connection (RAC) 管理員。 執行 RAC 管理員，並確定伺服器連線索引標籤在最上方。 接下來，尋找項目中的伺服器物件**OLE 類別**窗格並按一下它。 然後前往**網路位址**下拉式方塊並輸入遠端可執行檔執行所在的伺服器電腦名稱。 例如，您可以輸入\\\MyServer 這裡。 然後，從提供的清單中選擇適當的網路通訊協定。 您可能需要詢問您的網路系統管理員以判斷建議使用的通訊協定。 在大部分情況下，這會是 TCP/IP。 最後，您可以選擇驗證等級。 在大部分情況下，這會保留 (無) 或為預設值。 現在在伺服器上按一下滑鼠右鍵**OLE 類別**窗格。 在產生的捷徑功能表您可以選擇本機或遠端作業。 選取遠端。  
  
 步驟 3 是在選取的伺服器電腦或電腦上正確安裝和註冊伺服器應用程式。 如果應用程式在自我註冊，執行應用程式一次也會進行註冊。  
  
 第 4 步驟是將伺服器設定為允許遠端執行。 在伺服器電腦上執行 RAC 管理員，並確定**用戶端存取** 索引標籤有焦點。 選擇您想要啟用模型 (通常**允許依索引鍵的遠端建立**。 如果您選擇此選項，您也需要按一下**允許遠端啟用**核取方塊以設定的值為 'Y' 的登錄項目)。 如果您正在執行 Windows NT 或 Windows 2000，而您選擇允許遠端建立 (ACL)，您也可以選擇以編輯 ACL 推送**編輯 ACL**  按鈕。  
  
 若要允許遠 Remote Automation 運作，您必須確認已安裝 Automation 管理員，且已在伺服器電腦或電腦上執行。 如果尚未安裝，請複製 AUTMGR32.EXE 到 Windows 系統目錄。 如需如何執行這項操作的資訊，請參閱[遠端自動化安裝](../mfc/remote-automation-installation.md)。 若要啟動 Remote Automation，請執行 Automation 管理員。 如此將會出現一個小型狀態視窗，其中會顯示一些訊息。 一旦啟動，它將會自行最小化。 如果您想要繼續查看狀態資訊，您可以按一下**Automation 管理員**以還原視窗的工作列中的索引標籤。  
  
 最後一個步驟是在用戶端電腦執行用戶端應用程式。 如果有遵循上述步驟，就會連接到伺服器物件和精確地如在本機一樣地執行，但速度會慢一些。  
  
 請注意，RAC 管理員也可讓您在 Remote Automation 和分散式 COM (DCOM，在支援 DCOM 的平台) 之間利用選項按鈕進行切換。 如果選擇 DCOM，您可以設定各種組態選項。 如需詳細資訊，請參閱 DCOM 文件。  
  
## <a name="see-also"></a>請參閱  
 [Remote Automation](../mfc/remote-automation.md)   
 [使用 AUTOCLIK 和 AUTODRIV 執行 Remote Automation](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)

