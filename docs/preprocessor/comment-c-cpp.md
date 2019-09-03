---
title: comment pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 3175ad5318bcc6fd9aa6233258ccec9033c89be8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219092"
---
# <a name="comment-pragma"></a>comment pragma

將註解記錄放入目的檔或可執行檔中。

## <a name="syntax"></a>語法

> **#pragma 批註 (** *批註-類型*[ **,** "*批註字串*"] **)**

## <a name="remarks"></a>備註

*批註類型*是其中一個預先定義的識別碼 (如下所述), 其指定批註記錄的類型。 選擇性的*批註字串*是字串常值, 可提供某些批註類型的其他資訊。 因為*批註字串*是字串常值, 所以它會遵守有關逸出字元、內嵌引號 (`"`) 和串連的字串常值的所有規則。

### <a name="compiler"></a>編譯器

將編譯器的名稱和版本號碼放入目的檔中。 連結器會忽略這個註解記錄。 如果您為此記錄類型提供*批註字串*參數, 則編譯器會產生警告。

### <a name="lib"></a>lib

在目的檔中放入程式庫搜尋記錄。 此批註類型必須伴隨一個包含您想要連結器搜尋之程式庫名稱 (也可能是路徑) 的*批註字串*參數。 程式庫名稱會遵循物件檔案中的預設程式庫搜尋記錄;連結器會搜尋此媒體櫃, 就像您在命令列上已將它命名為, 前提是未使用[/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md)指定媒體櫃。 您可以在同一個原始程式檔中放入多個程式庫搜尋記錄，每一個記錄都會依照本身在原始程式檔中產生的順序出現在目的檔中。

如果預設程式庫和新增程式庫的順序很重要, 使用[/zl](../build/reference/zl-omit-default-library-name.md)參數進行編譯將會使預設程式庫名稱無法放在物件模組中。 然後就可以使用第二個註解 pragma 將預設程式庫的名稱插入已加入之程式庫的後面。 使用這些 pragma 列出的程式庫將依照它們在原始程式碼中的順序出現在物件模型中。

### <a name="linker"></a>連結器

將[連結器選項](../build/reference/linker-options.md)放在物件檔案中。 您可以使用這個註解類型指定連結器選項，而不要將其傳遞到命令列或是在開發環境中指定。 例如，您可以指定 /include 選項強制包含符號：

```C
#pragma comment(linker, "/include:__mySymbol")
```

只有下列 (*批註類型*) 連結器選項可以傳遞至連結器識別碼:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>user

將一般註解放入目的檔中。 *批註字串*參數包含批註的文字。 連結器會忽略這個註解記錄。

## <a name="examples"></a>範例

下列 pragma 會使連結器在連結時搜尋 EMAPI.LIB 程式庫。 連結器會先搜尋目前的工作目錄，然後再搜尋 LIB 環境變數中所指定的路徑。

```C
#pragma comment( lib, "emapi" )
```

下列 pragma 會讓編譯器將編譯器的名稱和版本號碼放入目的檔中：

```C
#pragma comment( compiler )
```

針對接受*批註字串*參數的批註, 您可以在任何要使用字串常值的地方使用宏, 前提是宏會展開為字串常值。 您也可以串連任何的組合，其中包括字串常值以及可展開為字串常值的巨集。 例如，以下是可接受的陳述式：

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
