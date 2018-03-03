---
title: "優點及用來連結到該 CRT 之方法的缺點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 244415a947918a836e8c4c67dbd18758ec40393c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>優點及用來連結到該 CRT 之方法的缺點
您的專案可以使用 CRT 連結，以動態方式或以靜態方式。 下表概述的優點和權衡取捨中選擇要使用的方法。  
  
|方法|優勢|權衡取捨|  
|------------|-------------|--------------|  
|以靜態方式連結到該 CRT<br /><br /> (**執行階段程式庫**設**單一執行緒**)|在執行映像所在系統上不需要 CRT DLL。|大約 25 K 的啟始程式碼加入至您的映像，大幅增加其大小。|  
|動態連結到該 CRT<br /><br /> (**執行階段程式庫**設**多執行緒**)|您的映像不需要 CRT 啟始程式碼，因此您很遠。|CRT DLL 必須在執行映像的系統上。|  
  
 本主題[連結至您的 ATL 專案中 CRT](../atl/linking-to-the-crt-in-your-atl-project.md)討論如何選取要進行連結到該 CRT 之方式。  
  
## <a name="see-also"></a>請參閱  
 [ATL 和 C 執行階段程式碼的程式設計](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Dll 和 Visual c + + 執行階段程式庫行為](../build/run-time-library-behavior.md)   
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)

