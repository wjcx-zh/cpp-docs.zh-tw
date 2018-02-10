---
title: "字元的優點設定可攜性 |Microsoft 文件"
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
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce02fa834c39f629990d4f3c9785de94bd02196
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="benefits-of-character-set-portability"></a>字元集移植性的優點
您可以從使用 MFC 與 C 執行階段可攜性功能，即使您目前不想要您的應用程式的國際化獲益：  
  
-   可移植，可讓您的程式碼基底彈性。 您可以稍後再將它輕鬆 MBCS 或 Unicode。  
  
-   使用 Unicode，可以讓 Windows 應用程式的效率。 因為 Windows 會使用 Unicode，非 Unicode 字串與作業系統之間來回必須轉譯，其帶來的額外負荷。  

  
## <a name="see-also"></a>請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [Unicode 的支援](../text/support-for-unicode.md)