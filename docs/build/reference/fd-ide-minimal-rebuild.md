---
title: -FD （IDE 最少重建） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e31955b131e4ca22d23013565e53f83493275d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (IDE 最少重建)
**/FD**不公開給使用者，除了在[命令列](../../ide/command-line-property-pages.md)c + + 專案屬性頁**屬性頁**對話方塊中，如果且只有[/Gm （啟用最少重建）](../../build/reference/gm-enable-minimal-rebuild.md)也未選取。 **/FD**以外沒有作用，從開發環境。 **/FD**的輸出中未公開**cl /？**。  
  
 如果您未啟用 **/Gm**在開發環境中， **/FD**將使用。 **/FD**可確保.idb 檔具有足夠的相依性資訊。 **/FD**只供開發環境中，不應使用從命令列或組建指令碼。  
  
## <a name="see-also"></a>另請參閱  
 [輸出檔 (/ F) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)