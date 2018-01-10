---
title: "字元的優點設定可攜性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 554137352c0a8f7275a051e4026020fce25edbb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="benefits-of-character-set-portability"></a>字元集移植性的優點
您可以從使用 MFC 與 C 執行階段可攜性功能，即使您目前不想要您的應用程式的國際化獲益：  
  
-   可移植，可讓您的程式碼基底彈性。 您可以稍後再將它輕鬆 MBCS 或 Unicode。  
  
-   使用 Unicode，可讓您的應用程式，適用於 Windows 2000 更有效率。 因為 Windows 2000 會使用 Unicode，非 Unicode 字串與作業系統之間來回必須轉譯，其帶來的額外負荷。  
  
-   使用 MBCS，可讓您在 Windows 2000 中，例如 Windows 95 或 Windows 98 以外的 Win32 平台上支援國際市場。  
  
## <a name="see-also"></a>請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [Unicode 的支援](../text/support-for-unicode.md)