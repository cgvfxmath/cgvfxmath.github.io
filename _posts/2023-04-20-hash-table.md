---
layout: post
title: "Hash Table"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'data structure', 'hash']
use_math: true
lastmode: 2023-04-20 11:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

It stores key-value pairs with fast access but collisions may occur.<!--more-->

해시 데이터 구조(hash data structure)는 키(key)와 값(value)을 저장하기 위한 자료 구조입니다. 해시 데이터 구조는 키와 값의 쌍을 연관 배열로 저장하며, 키를 사용하여 값에 빠르게 접근할 수 있습니다.

해시 데이터 구조는 키를 해시 함수(hash function)에 적용하여 고유한 인덱스를 생성하고, 이 인덱스를 사용하여 값을 저장하고 검색합니다. 해시 함수는 입력된 키를 고정된 길이의 해시 값으로 변환하는 함수입니다. 이 해시 값은 일반적으로 배열의 인덱스와 같은 형태로 사용됩니다. 해시 함수는 일반적으로 입력된 키에 대해 고유한 해시 값을 반환하도록 설계되어 있습니다.

해시 데이터 구조는 매우 빠른 검색 속도를 제공합니다. 일반적으로 해시 함수는 입력된 키에 대해 고유한 해시 값을 반환하므로, 이를 사용하여 값을 저장하고 검색할 때 별다른 탐색 작업 없이 빠르게 값을 찾을 수 있습니다.

하지만 해시 함수가 충돌을 일으키는 경우도 있습니다. 두 개 이상의 키가 동일한 해시 값으로 매핑되는 경우를 충돌이라고 합니다. 이러한 충돌을 처리하는 방법에는 여러 가지가 있습니다. 가장 일반적인 방법은 연결 리스트를 사용하여 충돌을 처리하는 것입니다. 이 방법은 같은 해시 값에 매핑되는 키들을 하나의 연결 리스트에 저장합니다.

해시 데이터 구조는 해시 테이블(hash table)이라는 배열을 사용하여 구현할 수 있습니다. 이러한 해시 테이블은 일반적으로 고정된 크기를 가지며, 충돌이 발생할 경우 연결 리스트를 사용하여 저장합니다. 해시 데이터 구조는 검색 작업에 매우 빠르며, 대부분의 언어에서 제공되는 표준 라이브러리에서 제공됩니다.

### hash table (or hash map)
* associated array: (key, value) 형식의 data를 저장하는 data structure
* hash function을 사용하여 입력 key 값으로부터 hash value를 얻은 다음 이를 index로 사용하여 associated array의 형태로 저장하는 자료구조
* hash table의 각 원소: bucket 또는 slot

### hash function
* 임의의 길이를 갖는 data를 고정된 길이의 data로 mapping하는 algorithm
* input: key value
* output: hash value
* 이상적인 hash function의 조건: (A's key value) != (B's key value) 이면 (A's hash value) != (B's hash value)

### hash collision
* 두 개 이상의 서로 다른 key값이 동일한 hash value로 mapping될 경우 발생

### hash collision을 해결하는 방법
* closed hashing: 처음에 주어진 hash table의 공간 안에서 문제를 해결하는 방식
* open hashing: 처음에 주어진 hash table의 공간 밖에 새로운 공간을 할당하여 문제를 해결하는 방식

### hash search
* chaining: 각각의 hash table index에 해당하는 자료구조를 linked list로 만들어서 관리하는 방법. bucket 내에서는 원하는 항목을 찾을 때 linked list를 순차 탐색
* 이상적인 hash size일 경우 만약 서로 다른 key 값이 서로 다른 hash value (index)로 mapping될 경우 hash table 조회에 걸리는 시간은 상수시간


