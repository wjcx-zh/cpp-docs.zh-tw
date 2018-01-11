---
title: "連結器工具錯誤 LNK1309 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1309
dev_langs: C++
helpviewer_keywords: LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 425fb564ae2bd099746fc9b76b496595caa10a0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1309"></a>連結器工具錯誤 LNK1309
type1 模組偵測到。交換器 /CLRIMAGETYPE:type2 無效  
  
 CLR 映像類型以要求**/CLRIMAGETYPE**但連結器無法產生該類型的映像，因為一個或多個模組是與該類型不相容。  
  
 例如，您會看到 LNK1309 如果您指定**/clrimagetype: safe**並傳遞模組，以建置**/clr: pure**。  
  
 如果您嘗試建置部分信任的 CLR 純虛擬應用程式，並使用 [d] ptrustu.lib，也會看到 LNK1309。 如需如何建立部分信任的應用程式資訊，請參閱[How to： 建立於 CRT 程式庫 DLL 的部分信任的應用程式以移除相依性](../../dotnet/create-a-partially-trusted-application.md)。  
  
 如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[/CLRIMAGETYPE （指定類型的 CLR 映像）](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。