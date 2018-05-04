---
title: -執行-字元集 （設定執行字元集） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bffe1e39aa181a6d53784fbb4501bf8f662b221
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="execution-charset-set-execution-character-set"></a>/execution-charset (設定執行 Character Set)
可讓您指定可執行檔的執行字元集。  
  
## <a name="syntax"></a>語法  
  
```  
/execution-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>引數  
 **IANA_name**  
 IANA 定義字元集名稱。  
  
 **CPID**  
 字碼頁識別項。  
  
## <a name="remarks"></a>備註  
 您可以使用 **/execution-charset**選項來指定執行字元集。 執行字元集是用於程式輸入至在所有前置處理步驟編譯階段的文字編碼方式。 這個字元集用於在已編譯的程式碼中任何字串或字元常值的內部表示法。 設定此選項來指定原始程式檔包含無法以基本執行字元集的字元時所要使用的擴充的執行字元集。 您可以使用任一 IANA 或 ISO 字元集的名稱，或點 （.） 後面接著指定要使用的字元集 3 到 5 位數十進位的字碼頁識別項。 一份支援程式碼頁面識別碼和字元集的名稱，請參閱[程式碼頁面識別碼](http://msdn.microsoft.com/library/windows/desktop/dd317756)。  
  
 根據預設，Visual Studio 會偵測來判斷來源檔案是否已編碼的 Unicode 格式，例如，utf-8 或 utf-16 位元組順序標記。 如果找到沒有位元組順序標記，它會假設來源檔案編碼使用目前使用者的字碼頁，除非您已指定為字元使用設定名稱或程式碼頁 **/source-charset**選項或 **/utf-8**選項。 Visual Studio 可讓您使用數種字元編碼的任何儲存您的 c + + 程式碼。 來源和執行字元集的相關資訊，請參閱[字元集](../../cpp/character-sets.md)語言文件中。  
  
 如果您想要設定來源字元集和執行字元集為 utf-8，您可以使用 **/utf-8**較快速的編譯器選項。 它相當於指定 **/來源-charset:utf-8 /execution-charset:utf-8**命令列上。 這些選項也可讓 **/validate-charset**預設選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**， **C/c + +**，**命令列**資料夾。  
  
3.  在**進階選項**，新增 **/execution-charset**選項，並指定您的慣用編碼方式。  
  
4.  選擇**確定**以儲存變更。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/source-charset (設定來源 Character Set)](../../build/reference/source-charset-set-source-character-set.md)   
 [/utf-8 （設定來源和可執行檔字元集為 utf-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset (驗證字元是否相容)](../../build/reference/validate-charset-validate-for-compatible-characters.md)