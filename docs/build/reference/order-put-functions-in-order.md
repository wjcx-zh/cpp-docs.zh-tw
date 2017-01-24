---
title: "/ORDER (依順序置放函式) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.FunctionOrder"
  - "/order"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ORDER 連結器選項"
  - "LINK 工具 [C++], 程式最佳化"
  - "LINK 工具 [C++], 交換微調"
  - "ORDER 連結器選項"
  - "-ORDER 連結器選項"
  - "分頁, 最佳化"
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ORDER (依順序置放函式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ORDER:@filename  
```  
  
## 參數  
 *filename*  
 是一個指定 COMDAT 函式連結順序的文字檔。  
  
## 備註  
 \/ORDER 選項會告訴 LINK 以預先決定的順序將某些 COMDAT 放入映像中，使您的程式最佳化。  LINK 會在映像的每一區段中將這些函式依指定的順序放置。  
  
 請在 *filename* 中指定順序，該檔案是一個文字檔 \(回應檔\)，它列出 COMDAT 的方式就是您希望連結它們的順序。  *filename* 中的每一行都包含一個 COMDAT 的名稱。  如果目的檔是以 \/Gy 選項編譯便含有 COMDAT。  函式名稱須區分大小寫。  
  
 LINK 會使用識別項的裝飾形式。  編譯器會在建立 .obj 檔時裝飾識別項。  當您需要向連結器指定識別項時，請使用 [DUMPBIN](../../build/reference/dumpbin-reference.md) 工具取得識別項的裝飾形式。  如需有關裝飾名稱的詳細資訊，請參閱[裝飾名稱](../../build/reference/decorated-names.md)。  
  
 如果使用了一個以上 \/ORDER 規格，只有最後指定的會生效。  
  
 利用調整放置順序，您可以將一個函式與該函式所呼叫的函式組成一個群組，進行透過這種交換調整方式，達到程式分頁行為最佳化的結果。  您也可以將經常呼叫的函式群組在一起。  這些技巧可以增加當您需要呼叫某個函式時它就在記憶體中而不需再從磁碟分頁的可能性。  
  
 連結器會在每個 *filename* 中的裝飾名稱前面加上底線 \(\_\)，除非該名稱是以問號 \(?\) 或 at 符號 \(@\) 開頭。  例如，假設目的檔含有 `extern "C" int func(int)` 和 `int main(void)`，DUMPBIN [\/SYMBOLS](../../build/reference/symbols.md) 會列出如下的裝飾名稱：  
  
```  
009 00000000 SECT3  notype ()    External     | _func  
00A 00000008 SECT3  notype ()    External     | _main  
```  
  
 但是，在順序檔中指定的名稱仍然應該是 `func` 和 `main`。  
  
 \/ORDER 選項會停用累加連結。  
  
> [!NOTE]
>  LINK 無法為靜態函式排序，因為靜態函式的名稱並非公用符號名稱。  指定了 \/ORDER 之後，連結器會對順序檔中每一個靜態或找不到的符號發出 LNK4037 警告。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[最佳化\] 屬性頁。  
  
4.  修改 \[函式順序\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)