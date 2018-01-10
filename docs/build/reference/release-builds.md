---
title: "發行組建 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12e81b26cd83214a5d62a42689bfc3a866ef1c10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="release-builds"></a>發行的組建
發行組建會使用最佳化。 當您使用最佳化來建立發行組建時，編譯器不會產生符號偵錯資訊。 呼叫的符號偵錯資訊的詳細資訊，以及追蹤和判斷提示不產生程式碼的事實不存在，表示可執行檔的大小會減少，並因此將會比較快。  
  
 本節提供有關您為何和何時要將變更從偵錯組建為發行組建資訊。 它也會討論一些您在偵錯從變更的發行組建時可能會遇到的問題：  
  
-   [建立發行組建](../../build/reference/how-to-create-a-release-build.md)  
  
-   [建立發行組建時的常見問題](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)  
  
    -   [檢查 ASSERT 陳述式](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [使用偵錯版檢查記憶體覆寫](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [偵錯發行組建](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [檢查記憶體覆寫](../../build/reference/checking-for-memory-overwrites.md)  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中建置 c + + 專案](../../ide/building-cpp-projects-in-visual-studio.md)   
 [C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)