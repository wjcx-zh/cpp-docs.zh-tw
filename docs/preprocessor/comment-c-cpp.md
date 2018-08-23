---
title: 註解 （C/c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.comment
- comment_CPP
dev_langs:
- C++
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d90cdb457e09ca51f14828daf5b7fb2676cb0db
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539963"
---
# <a name="comment-cc"></a>comment (C/C++)
將註解記錄放入目的檔或可執行檔中。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## <a name="remarks"></a>備註 

*註解類型*是其中一個預先定義的識別碼，如下所述，可指定註解記錄類型。 選擇性*commentstring*是字串常值，提供部分註解類型的其他資訊。 因為*commentstring*是字串常值，它會遵守字串常值的逸出字元，內嵌的引號內的所有規則 (`"`)，和串連。  
  
### <a name="compiler"></a>編譯器  
將編譯器的名稱和版本號碼放入目的檔中。 連結器會忽略這個註解記錄。 如果您提供*commentstring*參數，此記錄的類型，編譯器會產生警告。  
  
### <a name="exestr"></a>exestr  
上的芳鄰*commentstring*目的檔中。 在連結階段，這個字串會放入可執行檔中。 字串不會在載入可執行檔時一併載入記憶體中，不過，當程式在檔案中尋找可列印字串時就可以找到這些字串。 這個 comment-record 類型的其中一種用法，是在可執行檔中內嵌版本號碼或類似的資訊。  
  
`exestr` 已被取代，將在未來版本中移除。連結器不會處理註解記錄。  
  
### <a name="lib"></a>lib  
在目的檔中放入程式庫搜尋記錄。 這個註解類型必須伴隨著*commentstring*參數，其中包含的名稱 （與可能的路徑） 您想要連結器搜尋的程式庫。 程式庫名稱會遵循目的檔; 中的預設程式庫搜尋記錄就如同您命名為它在命令列上，提供程式庫中未指定，連結器搜尋此媒體櫃[/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md)。 您可以在同一個原始程式檔中放入多個程式庫搜尋記錄，每一個記錄都會依照本身在原始程式檔中產生的順序出現在目的檔中。  
  
如果預設程式庫和加入之程式庫的順序很重要，以編譯[/Zl](../build/reference/zl-omit-default-library-name.md)交換器會造成無法放入物件模組的預設程式庫名稱。 然後就可以使用第二個註解 pragma 將預設程式庫的名稱插入已加入之程式庫的後面。 使用這些 pragma 列出的程式庫將依照它們在原始程式碼中的順序出現在物件模型中。  
  
### <a name="linker"></a>連結器  
上的芳鄰[連結器選項](../build/reference/linker-options.md)目的檔中。 您可以使用這個註解類型指定連結器選項，而不要將其傳遞到命令列或是在開發環境中指定。 例如，您可以指定 /include 選項強制包含符號：  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
只有下列 (*註解類型*) 連結器選項可用於傳遞至連結器識別項：  
  
- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
- [/EXPORT](../build/reference/export-exports-a-function.md)  
  
- [/INCLUDE](../build/reference/include-force-symbol-references.md)  
  
- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
- [/ 合併](../build/reference/merge-combine-sections.md)  
  
- [/SECTION](../build/reference/section-specify-section-attributes.md)  
  
### <a name="user"></a>使用者  
將一般註解放入目的檔中。 *Commentstring*參數包含註解的文字。 連結器會忽略這個註解記錄。  
  
下列 pragma 會使連結器在連結時搜尋 EMAPI.LIB 程式庫。 連結器會先搜尋目前的工作目錄，然後再搜尋 LIB 環境變數中所指定的路徑。  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
下列 pragma 會讓編譯器將編譯器的名稱和版本號碼放入目的檔中：  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
> 針對註解會採用*commentstring*參數，您可以在任何位置，您會在此使用字串常值，使用巨集，前提巨集會展開為字串常值。 您也可以串連任何的組合，其中包括字串常值以及可展開為字串常值的巨集。 例如，以下是可接受的陳述式：  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## <a name="see-also"></a>另請參閱  
 
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)