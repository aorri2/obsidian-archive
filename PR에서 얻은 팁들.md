- 객체를 찾는데 없을 경우 객체를  새로  생성하고 싶을때는 get_or_create사용 고려
- dict 타입 사용시 keyerror같은게 발생할 수 있으니 예외처리에 신경쓰기
- some_obj == True 또는 some_obj == False 같은 구문 대신
- if some_obj : 또는 if not some_obj와 같이 체크하는게 더 보기 좋음
- update_or_create같은 경우도 고려해보기(ex. 없으면 생성 있으면 업데이트)
- _ 같은 경우 장고 번역에서 사용할 수도 있기에 겹치지 않도록 변수 사용시 주의
- 