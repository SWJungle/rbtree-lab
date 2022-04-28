# Red-Black Tree 구현

Balanced search tree로 많이 쓰이는 Red-black tree (이하 RB tree)를 C 언어로 구현하는 과제입니다.
구현하는 추상 자료형 (ADT: abstract data type)은 ordered set, multiset 입니다.

## 구현 범위
다음 기능들을 수행할 수 있도록 RB tree를 구현합니다.

- tree = `new_tree()`: RB tree 구조체 생성
  - 여러 개의 tree를 생성할 수 있어야 하며 각각 다른 내용들을 저장할 수 있어야 합니다.
- `delete_tree(tree)`: RB tree 구조체가 차지했던 메모리 반환
  - 해당 tree가 사용했던 메모리를 전부 반환해야 합니다. (valgrind로 나타나지 않아야 함)

- `tree_insert(tree, key)`: key 추가
  - 구현하는 ADT가 multiset이므로 이미 같은 key의 값이 존재해도 하나 더 추가 합니다.
- ptr = `tree_find(tree, key)`
  - RB tree내에 해당 key가 있는지 탐색하여 있으면 해당 node pointer 반환
  - 해당하는 node가 없으면 NULL 반환
- `tree_erase(tree, ptr)`: RB tree 내부의 ptr로 지정된 node를 삭제하고 메모리 반환
- ptr = `tree_min(tree)`: RB tree 중 최소 값을 가진 node pointer 반환
- ptr = `tree_max(tree)`: 최대값을 가진 node pointer 반환

- `tree_to_array(tree, array, n)`
  - RB tree의 내용을 *key 순서대로* 주어진 array로 변환
  - array의 크기는 n으로 주어지며 tree의 크기가 n 보다 큰 경우에는 순서대로 n개 까지만 변환
  - array의 메모리 공간은 이 함수를 부르는 쪽에서 준비하고 그 크기를 n으로 알려줍니다.

## 구현 규칙
- `src/rbtree.c` 이외에는 수정하지 않고 test를 통과해야 합니다.
- `make test`를 수행하여 `Passed All tests!`라는 메시지가 나오면 모든 test를 통과한 것입니다.
- Sentinel node를 사용하여 구현했다면 `test/Makefile`에서 `CFLAGS` 변수에 `-DSENTINEL`이 추가되도록 comment를 제거해 줍니다.

## 과제의 의도 (Motivation)

- 복잡한 자료구조(data structure)를 구현해 봄으로써 자신감 상승
- C 언어, 특히 포인터(pointer)와 malloc, free 등의 system call에 익숙해짐.
- 동적 메모리 할당(dynamic memory allocation)을 직접 사용해 봄으로써 동적 메모리 할당의 필요성 체감 및 data segment에 대한 이해도 상승
- 고급 언어에서 기본으로 제공되는 자료구조가 세부적으로는 어떻게 구현되어 있는지 경험함으로써 고급 언어 사용시에도 효율성 고려

## 참고문헌
- [위키백과: 레드-블랙 트리](https://ko.wikipedia.org/wiki/%EB%A0%88%EB%93%9C-%EB%B8%94%EB%9E%99_%ED%8A%B8%EB%A6%AC)
([영어](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree))
- CLRS book (Introduction to Algorithms) 13장 레드 블랙 트리 - Sentinel node를 사용한 구현
- [Wikipedia:균형 이진 트리의 구현 방법들](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree#Implementations)
