---
title: 登錄指令碼範例 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c192e8bec1d32dd7d7a7953e5da72a139c7520e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="registry-scripting-examples"></a>登錄指令碼範例
本主題中的指令碼範例將示範如何新增到系統登錄機碼、 註冊 COM 註冊機構的伺服器，以及指定多個剖析樹狀結構。  
  
## <a name="add-a-key-to-hkeycurrentuser"></a>新增 HKEY_CURRENT_USER 機碼  
 下列剖析樹狀目錄說明簡單的指令碼，將單一索引鍵加入至系統登錄。 特別是，指令碼會將索引鍵，`MyVeryOwnKey`至`HKEY_CURRENT_USER`。 它也會將指派的預設字串值`HowGoesIt`新機碼：  
  
```  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
 此指令碼可以輕鬆地擴充來定義多個子機碼，如下所示：  
  
```  
HKCU  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
 {  
 'HasASubkey'  
 {  
 'PrettyCool' = d '55'  
    val 'ANameValue' = s 'WithANamedValue'  
 }  
 }  
}  
```  
  
 現在，指令碼會新增子機碼，`HasASubkey`至`MyVeryOwnKey`。 這個子機碼，它將兩者`PrettyCool`子機碼 (預設值`DWORD`55 的值) 和`ANameValue`名稱為 value (具有字串值的`WithANamedValue`)。  
  
##  <a name="_atl_register_the_registrar_com_server"></a> 登錄註冊機構 COM 伺服器  
 下列指令碼會註冊本身的註冊機構 COM 伺服器。  
  
```  
HKCR  
{  
    ATL.Registrar = s 'ATL Registrar Class'  
 {  
    CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
 }  
    NoRemove CLSID  
 {  
    ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = 
    s 'ATL Registrar Class'  
 {  
    ProgID = s 'ATL.Registrar'  
    InprocServer32 = s '%MODULE%'  
 {  
    val ThreadingModel = s 'Apartment'  
 }  
 }  
 }  
}  
```  
  
 在執行階段，將此剖析樹狀目錄`ATL.Registrar`鍵`HKEY_CLASSES_ROOT`。 這個新的索引鍵，然後：  
  
-   指定`ATL Registrar Class`做為索引鍵的預設字串值。  
  
-   新增`CLSID`做為子機碼。  
  
-   指定`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`如`CLSID`。 (這個值會在註冊機構搭配 CLSID `CoCreateInstance`。)  
  
 因為`CLSID`是共用的它應該不會移除在取消註冊模式下。 陳述式， `NoRemove CLSID`，做法是，表示`CLSID`應該在註冊模式中開啟並忽略以取消註冊模式。  
  
 `ForceRemove`陳述式提供環境維護函式，藉由移除再重新建立索引鍵的索引鍵和所有子機碼。 這可以是如果子機碼名稱已變更。 在此指令碼的範例中，`ForceRemove`檢查`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`已經存在。 若是如此， `ForceRemove`:  
  
-   以遞迴方式刪除`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`和所有子機碼。  
  
-   重新建立`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。  
  
-   新增`ATL Registrar Class`做為預設字串值`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。  
  
 剖析樹狀結構現在會將兩個新的子機碼以`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。 第一個索引鍵， `ProgID`，取得 ProgID 的預設字串值。 第二個索引鍵， `InprocServer32`，取得的預設字串值， `%MODULE%`，也就是前置處理器值中，說明[使用可置換的參數 （登錄器的前置處理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)，這篇文章。 `InprocServer32` 也會取得一個具名的值， `ThreadingModel`，字串值是`Apartment`。  
  
## <a name="specify-multiple-parse-trees"></a>指定多個剖析樹狀結構  
 若要在指令碼中指定一個以上的剖析樹狀目錄，只要將一個樹狀結構的另一端。 例如，下列指令碼會將索引鍵， `MyVeryOwnKey`，同時剖析樹狀結構至`HKEY_CLASSES_ROOT`和`HKEY_CURRENT_USER`:  
  
```  
HKCR  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
> [!NOTE]
>  登錄器指令碼，在 4 K 是語彙基元的大小上限。 （語彙基元是任何可辨識的項目語法中）。在先前的指令碼範例中， `HKCR`， `HKEY_CURRENT_USER`， `'MyVeryOwnKey'`，和`'HowGoesIt'`是所有的語彙基元。  
  
## <a name="see-also"></a>另請參閱  
 [建立登錄器指令碼](../atl/creating-registrar-scripts.md)

