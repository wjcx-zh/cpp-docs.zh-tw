---
title: 字元的優點設定可攜性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1b78048baebfd89aed0ccc898c2bb9e3612525
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="benefits-of-character-set-portability"></a>字元集移植性的優點
您可以從使用 MFC 與 C 執行階段可攜性功能，即使您目前不想要您的應用程式的國際化獲益：  
  
-   可移植，可讓您的程式碼基底彈性。 您可以稍後再將它輕鬆 MBCS 或 Unicode。  
  
-   使用 Unicode，可以讓 Windows 應用程式的效率。 因為 Windows 會使用 Unicode，非 Unicode 字串與作業系統之間來回必須轉譯，其帶來的額外負荷。  

  
## <a name="see-also"></a>另請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [Unicode 的支援](../text/support-for-unicode.md)