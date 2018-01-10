---
title: "疑難排解組建自訂 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5fa3b2d3910a71d189f5177e13fbd91930e15ee8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="troubleshooting-build-customizations"></a>疑難排解組建自訂
如果您的自訂建置步驟或事件行為如預期般，，有幾件事，您可以嘗試了解什麼錯誤。  
  
-   請確定您的自訂建置步驟所產生的檔案相符的宣告為輸出的檔案。  
  
-   如果您的自訂建置步驟會產生為輸入的任何檔案或其他相依性建立 （自訂或其他） 的步驟，請確定這些檔案會加入至您的專案。 請使用這些檔案的工具執行自訂建置步驟之後。  
  
-   若要顯示實際進行什麼自訂建置步驟，新增`@echo on`做為第一個命令。 建置事件與建置步驟會放在暫存.bat 檔案，並執行建置專案時。 因此，您可以加入錯誤檢查，以建置事件，或建置步驟的命令。  
  
-   檢查組建記錄檔中的中繼檔案目錄，以查看實際執行的內容。 組建記錄檔的名稱與路徑由**MSBuild**巨集運算式**$ （intdir)\\$(MSBuildProjectName).log**。  
  
-   修改您的專案設定來收集多個預設數量的組建記錄檔中的資訊。 在 [ **工具** ] 功能表上按一下 [ **選項**]。 在**選項**對話方塊中，按一下 **專案和方案**節點，然後按一下**建置並執行**節點。 然後，在**MSBuild 專案組建記錄檔詳細等級**方塊中，按一下**Detailed**。  
  
-   請確認檔案正在使用的名稱或目錄巨集的任何值。 您可以個別回應巨集，或者您可以加入`copy %0 command.bat`開始自訂建置步驟時，這將複製至 command.bat 自訂建置步驟的命令與所有展開的巨集。  
  
-   執行自訂建置步驟，並建置分別可檢查其行為的事件。  
  
## <a name="see-also"></a>請參閱  
 [了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)