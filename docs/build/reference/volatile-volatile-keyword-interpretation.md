---
title: "-volatile （volatile 關鍵字轉譯） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs: C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0e5d138f93aad3603215c3268c2723e0d421b84d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (volatile 關鍵字轉譯)
指定如何[volatile](../../cpp/volatile-cpp.md)關鍵字會被解譯。  
  
## <a name="syntax"></a>語法  
  
```  
/volatile:{iso|ms}  
```  
  
## <a name="arguments"></a>引數  
 **/volatile:iso**  
 選取嚴格`volatile`ISO 標準 c + + 語言所定義的語意。 暫時性存取不保證 acquire/release 語意。 如果編譯器會以 ARM 為目標，這是預設解譯`volatile`。  
  
 **/volatile: ms**  
 選取 Microsoft 擴充`volatile`新增記憶體排序保證以外的 ISO 標準 c + + 語言的語意。 暫時性存取保證 acquire/release 語意。 不過，此選項也會強制編譯器產生的硬體記憶體屏障，可能會顯著增加負擔，在 ARM 和其他記憶體排序的弱式架構。 如果 ARM 以外的任何平台為目標的編譯器，這是預設解譯`volatile`。  
  
## <a name="remarks"></a>備註  
 我們強烈建議您改用**/volatile:iso**以及明確的同步處理基本類型和編譯器內建在處理跨執行緒共用的記憶體時。 如需詳細資訊，請參閱[volatile](../../cpp/volatile-cpp.md)。  
  
 如果您現有的程式碼移植，或變更此專案的中間選項，可能會很有幫助啟用警告[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)來識別受影響的語意差異的程式碼位置。  
  
 沒有任何`#pragma`相當於控制這個選項。  
  
### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>若要設定 /volatile 編譯器選項在 Visual Studio 中  
  
1.  開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  在**其他選項**方塊中，加入`/volatile:iso`或`/volatile:ms`。  
  
## <a name="see-also"></a>另請參閱  
 [volatile](../../cpp/volatile-cpp.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)