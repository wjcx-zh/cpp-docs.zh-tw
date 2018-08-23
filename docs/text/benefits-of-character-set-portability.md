---
title: 字元的優點將可攜性 |Microsoft Docs
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b812b0712e6df24422ebe4a3b73376619051b484
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586801"
---
# <a name="benefits-of-character-set-portability"></a>字元集移植性的優點
您可以使用 MFC 和 C 執行階段可攜性功能，即使您目前不想要您的應用程式的國際化獲益：  
  
-   可移植，可讓您的程式碼基底彈性。 您可以稍後再將它輕鬆地 Unicode 或 MBCS。  
  
-   使用 Unicode，可讓您的應用程式的 Windows 更有效率。 因為 Windows 會使用 Unicode，非 Unicode 字串與作業系統之間來回必須轉譯，這會產生額外負荷。  

  
## <a name="see-also"></a>另請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [Unicode 的支援](../text/support-for-unicode.md)