---
title: "DCOM 的歷史 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation, DCOM
- DCOM, about DCOM
- DCOM
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9e5607fd240c7a97691189b8a3afa5e7c0171e26
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="history-of-dcom"></a>DCOM 的歷史
當早期 1993年引進自動化時，它是能夠只會在相同電腦上執行的應用程式之間所使用。 不過，因為它共用相同的 underpinnings OLE，也就是說，COM （或元件物件模型） 的其他部分，它一律是 COM 本身已更新為包含遠端執行功能時，它會變成 「 遠端 」。 它也計劃純粹的本機作業轉換至分散式作業需要少量或沒有現有的程式碼變更。  
  
 讓介面的取用者位於 「 遠端 」 代表什麼本機 COM 規定，並為該介面的提供者在相同電腦上執行。 例如，Microsoft Visual Basic 無法控制在桌面的電腦上的 Microsoft Excel 複本，但並非能夠導向另一部電腦上執行的 Excel。 分散式 COM 開發，介面的取用者不再需要的介面提供者執行所在的同一部機器上。  
  
 一旦 COM 已在網路上運作，然後任何介面未以本機執行模型繫結 (某些介面本身必須仰賴本機電腦的功能，例如繪圖介面的方法有做為裝置內容控制代碼參數） 必須散發的功能。 介面取用者會使指定的介面; 的要求一部電腦上執行之物件 （或執行） 執行個體可提供該介面。 COM 內的散發機制會連接的方式提供者取用者，取用者所做的方法呼叫會出現在提供者結束時，就會執行。 任何傳回值都會送回給取用者。 不管您的目的，發佈的動作是透明消費者和提供者。  
  
 這類各種不同的 COM 現已存在。 DCOM （適用於 「 分散式 COM 」) 來一直隨附的 Windows NT 4.0 版開始，包括 Windows 2000 的版本。 自晚期 1996 年，它也有提供適用於 Windows 9x x。 在這兩種情況下，DCOM 會包含一組取代和其他 Dll、 與某些公用程式提供本機和遠端 COM 功能。 它現在是因此 win32 平台的固有部分，並可供其他平台上的其他組織一段時間。  
  
## <a name="in-this-section"></a>本章節內容  
 [沒有 Remote Automation 適用於什麼情況](where-does-remote-automation-fit-in-q.md)  
  
 [Remote Automation 提供什麼功能](what-does-remote-automation-provide-q.md)  
  
## <a name="see-also"></a>另請參閱  
 [Remote Automation](../mfc/remote-automation.md)
