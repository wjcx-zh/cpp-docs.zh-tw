---
title: "應用程式定義域和 Visual c + + |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57a45bd6f73040623fe90626b1c3896df3258dd8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="application-domains-and-visual-c"></a>應用程式定義域和 Visual C++
如果您有`__clrcall`虛擬函式，每個應用程式定義域 (appdomain)，將會在 vtable。 如果您在一個 appdomain 中建立物件，您只可以呼叫該 appdomain 內的虛擬函式。 中定義的所有函式**/clr: pure**編譯使用`__clrcall`呼叫慣例。 因此，所有的 vtable，定義在**/clr: pure**編譯是以每個 appdomain。 在混合模式 (**/clr**) 如果您的型別沒有任何，會有每個處理序 vtable`__clrcall`虛擬函式。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 如需詳細資訊，請參閱  
  
-   [appdomain](../cpp/appdomain.md)  
  
-   [__clrcall](../cpp/clrcall.md)  
  
-   [如何： 移轉至 /clr: pure (C + + /CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [process](../cpp/process.md)  
  
## <a name="see-also"></a>另請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)