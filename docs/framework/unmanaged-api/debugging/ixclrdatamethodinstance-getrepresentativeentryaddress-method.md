---
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress 메서드'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: d546cda5c68732e75550a3de286089f7df261c91
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420905"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a>IXCLRDataMethodInstance:: GetRepresentativeEntryAddress 메서드

메서드에 대 한 모든 가능한 진입점의 네이티브 컴파일에 대 한 가장 대표적인 진입점 주소를 가져옵니다.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>구문

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a>매개 변수

`addr`\
제한이 메서드에 대 한 가장 대표적인 기본 진입점의 주소입니다.

## <a name="remarks"></a>설명

제공 된 메서드는 [ `IXCLRDataMethodInstance` 인터페이스](ixclrdatamethodinstance-interface.md) 의 일부 이며 가상 메서드 테이블의 20 슬롯에 해당 합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
**헤더:** 없음을  
**라이브러리:** 없음을  
**.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>참고 항목

- [디버깅](index.md)
- [IXCLRDataMethodInstance 인터페이스](ixclrdatamethodinstance-interface.md)
