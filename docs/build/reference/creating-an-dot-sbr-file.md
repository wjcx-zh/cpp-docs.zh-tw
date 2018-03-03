---
title: "建立。Sbr 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d87b71daaf5d7b37e67c2c0e56e844bd5251a490
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-sbr-file"></a>建立 .Sbr 檔
BSCMAKE 的輸入的檔是.sbr 檔案。 編譯器會建立.sbr 檔案以供在編譯每個目的檔 (.obj)。 當您建立或更新您的瀏覽資訊檔時，為您的專案的所有.sbr 檔必須都是可用磁碟空間。  
  
 若要建立的.sbr 檔與所有可能的資訊，請指定[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)。  
  
 若要建立不含本機符號的.sbr 檔案，請指定[/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)。 如果.sbr 檔包含本機符號時，您可以仍然省略它們從.bsc 檔使用 BSCMAKE 的[/El 選項](../../build/reference/bscmake-options.md)`.`  
  
 您可以建立的.sbr 檔案而不執行完整的編譯。 例如，您可以指定 /Zs 選項，編譯器將執行語法檢查以及仍產生的.sbr 檔案，如果您指定 /FR 的話。  
  
 在建置程序可以更有效率的.sbr 檔案會先封裝移除未參考的定義。 編譯器會自動套件.sbr 檔案。  
  
## <a name="see-also"></a>請參閱  
 [建置 .Bsc 檔](../../build/reference/building-a-dot-bsc-file.md)