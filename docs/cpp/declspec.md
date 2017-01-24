---
title: "__declspec | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__declspec_cpp"
  - "__declspec"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++]"
ms.assetid: 832db681-e8e1-41ca-b78c-cd9d265cdb87
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __declspec
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 用於指定儲存類別資訊的擴充屬性語法是使用 `__declspec` 關鍵字，這會指定特定類型的執行個體要與以下所列的 Microsoft 專有儲存類別屬性儲存在一起。  其他儲存類別修飾詞的範例包括 `static` 和 `extern` 關鍵字。  不過，這些關鍵字是 C 和 C\+\+ 語言的 ANSI 規格的一部分，因此擴充屬性語法未涵蓋它們。  擴充屬性語法可簡化並標準化 Microsoft 專有的 C 和 C\+\+ 語言擴充功能。  
  
## 文法  
 *decl\-specifier*:  
 `__declspec (`  *extended\-decl\-modifier\-seq*  `)`  
  
 *extended\-decl\-modifier\-seq*:  
 *extended\-decl\-modifier* opt  
  
 *extended\-decl\-modifier extended\-decl\-modifier\-seq*  
  
 *extended\-decl\-modifier*:  
 `align(` *\#* `)`  
  
 `allocate("` *segname* `")`  
  
 `appdomain`  
  
 `code_seg("` *segname* `")`  
  
 `deprecated`  
  
 `dllimport`  
  
 `dllexport`  
  
 `jitintrinsic`  
  
 `naked`  
  
 `noalias`  
  
 `noinline`  
  
 `noreturn`  
  
 `nothrow`  
  
 `novtable`  
  
 `process`  
  
 `property(`{`get=`*get\_func\_name*&#124;`,put=`*put\_func\_name*}`)`  
  
 `restrict`  
  
 `safebuffers`  
  
 `selectany`  
  
 `thread`  
  
 `uuid("` *ComObjectGUID* `")`  
  
 空白字元會分隔宣告修飾詞序列。  範例會在後面的章節中顯示。  
  
 擴充屬性文法支援下列 Microsoft 特定的儲存類別屬性：[align](../cpp/align-cpp.md)、[allocate](../cpp/allocate.md)、[appdomain](../cpp/appdomain.md)、[code\_seg](../cpp/code-seg-declspec.md)、[deprecated](../cpp/deprecated-cpp.md)、[dllexport](../cpp/dllexport-dllimport.md)、[dllimport](../cpp/dllexport-dllimport.md)、[jitintrinsic](../cpp/jitintrinsic.md)、[naked](../cpp/naked-cpp.md)、[noalias](../cpp/noalias.md)、[noinline](../cpp/noinline.md)、[noreturn](../cpp/noreturn.md)、[nothrow](../cpp/nothrow-cpp.md)、[novtable](../cpp/novtable.md)、[process](../cpp/process.md)、[restrict](../cpp/restrict.md)、[safebuffers](../cpp/safebuffers.md)、[selectany](../cpp/selectany.md) 和 [thread](../cpp/thread.md)。  它也支援這些 COM 物件屬性：[property](../cpp/property-cpp.md) 和 [uuid](../cpp/uuid-cpp.md)。  
  
 `code_seg`、`dllexport`、`dllimport`、`naked`、`noalias`、`nothrow`、`property`、`restrict`、`selectany`、`thread` 和 `uuid` 儲存類別屬性 \(屬性\) 只是物件宣告或套用這些屬性 \(attribute\) 之函式宣告的屬性 \(property\)。  `thread` 屬性只會影響資料和物件。  `naked` 屬性只會影響函式。  `dllimport` 和 `dllexport` 屬性會影響函式、資料和物件。  `property`、`selectany` 和 `uuid` 屬性會影響 COM 物件。  
  
 `__declspec` 關鍵字應該放置在簡單宣告的開頭。  編譯器會忽略位在宣告中 \* 或 & 後面的任何 `__declspec` 關鍵字，以及位在宣告中變數識別項前面的這類關鍵字，不顯示警告。  
  
 使用者定義類型宣告開頭所指定的 `__declspec` 屬性會套用至該類型的變數。  例如：  
  
```  
__declspec(dllimport) class X {} varX;  
```  
  
 在本案例中，屬性會套用至 `varX`。  `__declspec` 屬性會放在 `class` 或 `struct` 關鍵字後面，適用於使用者定義類型。  例如：  
  
```  
class __declspec(dllimport) X {};  
```  
  
 在本案例中，屬性會套用至 `X`。  
  
 簡單宣告之 `__declspec` 屬性的一般使用方針如下：  
  
```  
  
decl-specifier-seq declarator-list;  
```  
  
 此外，*decl\-specifier\-seq* 必須包含基底類型 \(例如，  `int`、`float`、`typedef` 或類別名稱\)、儲存類別 \(例如，  `static`、`extern`\) 或 `__declspec` 擴充功能。  此外，*init\-declarator\-list* 必須包含宣告的指標部分。  例如：  
  
```  
__declspec(selectany) int * pi1 = 0;   //OK, selectany & int both part of decl-specifier  
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier  
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator  
```  
  
 下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：  
  
```  
// Example of the __declspec keyword  
__declspec( thread ) int tls_i = 1;  
```  
  
## END Microsoft 特定的  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)