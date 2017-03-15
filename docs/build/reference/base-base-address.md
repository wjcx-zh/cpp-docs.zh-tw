---
title: "/BASE (基底位址) | Microsoft Docs"
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
  - "/base"
  - "VC.Project.VCLinkerTool.BaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/BASE 連結器選項"
  - "基底位址的 @ 符號"
  - "基底位址的 @ 符號"
  - "基底位址 [C++]"
  - "BASE 連結器選項"
  - "-BASE 連結器選項"
  - "DLL [C++], 連結"
  - "環境變數 [C++], LIB"
  - "可執行檔 [C++], 基底位址"
  - "主要位址大小"
  - "LIB 環境變數"
  - "程式 [C++], 基底位址"
  - "程式 [C++], 防止重新配置"
  - "冒號 [C++], 規範"
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
caps.latest.revision: 15
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /BASE (基底位址)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/BASE:{address[,size] | @filename,key}  
```  
  
 \/BASE 選項會設定程式的基底位址，覆寫 .exe 檔 \(位於 0x400000\) 或 DLL \(位於 0x10000000\) 的預設位置。  作業系統首先會嘗試在指定或預設的基底位址載入程式。  如果在那裡沒有足夠的空間，那麼系統便會重新配置該程式。  若要防止重新配置，請使用 [\/FIXED](../../build/reference/fixed-fixed-base-address.md) 選項。  
  
 此種連結器會在 *address* 不是 64K 的倍數時發出錯誤訊息。您可以選擇性地指定程式的大小，如果程式無法符合指定的大小，連結器就會發出警告。  
  
 另一種在命令列上指定基底位址的方式是，在檔案中使用前面加上 at 符號 \(@\) 的 *filename* 和 `key`。  *filename* 是一個文字檔，含有程式要使用的所有 DLL 的位置和大小。  連結器會在指定的路徑或在 \(如果沒有指定路徑\) LIB 環境變數裡所指定的目錄中尋找 *filename*。  *filename* 中的每一行都代表一個 DLL 並且具有下列語法：  
  
```  
  
key address [size] ;comment  
```  
  
 `key` 是一個英數字元的字串而且不區分大小寫。  它通常是 DLL 的名稱，不過並非必須如此。  `key` 後面跟著一個以 C 語言、十六進位或十進位標記法表示的基底 *address*，以及選用性的最大 `size`。  這三個引數都是以空格或 Tab 字元分隔。  如果指定的 `size` 小於程式所需的虛擬位址空間，連結器便會發出警告。  `comment` 是以一個分號 \(;\) 指定，可以在同一行也可以在另一行。  連結器會忽略從分號開始到行尾的所有文字。  以下範例所示就是這類檔案的一部分：  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 假設含有這些行的檔案稱為 DLLS.txt，下列範例命令便會套用這項資訊：  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## 備註  
 您可以藉由指派基底位址讓 DLL 在位址空間中不會重疊，以減少分頁和增進程式的效能。  
  
 另一種設定基底位址的方式是使用 [NAME](../../build/reference/name-c-cpp.md) 或 [LIBRARY](../../build/reference/library.md) 陳述式中的 *BASE* 引數。  \/BASE 和 [\/DLL](../../build/reference/dll-build-a-dll.md) 選項合在一起就相當於 **LIBRARY** 陳述式。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[基底位址\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)