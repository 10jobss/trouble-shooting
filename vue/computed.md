# Unexpected side effect in computed property
목적 : 컴포넌트A(cmp-a), 컴포넌트 B(cmp-b)가 있다고 가정
       cmp_a에 선택된 값에 따라 cmp_b를 default value로 setting 및 disabled

computed에 다른 data를 변경했기 때문
computed에 정의된 flag를 watch에 추가해주는것으로 해결

참고 : 

as-is
```javascript
<cmp-a>...</cmp-a>
<cmp-b>
...
:disabled="flag"
</cmp-b>

<script>
computed: {
    flag() {
        if(this.componentData.selectedCodeValue.a_code.key !== 'X') {
            this.componentData.selectedCodeValue.b_code.first.key = 'Y';
            this.componentData.selectedCodeVAlue.b_code.second.key = 'Z';
        }
        return !utils.isEqual(this.componentData.selectedCodeValue.a_code.key, 'X');
    }
}
</script>
```

to-be
```javascript
<cmp-a>...</cmp-a>
<cmp-b>
...
:disabled="flag"
</cmp-b>

<script>
computed: {
    flag() {
        return !utils.isEqual(this.componentData.selectedCodeValue.a_code.key, 'X');
    }
}
watch: {
    flag() {
        if(this.componentData.selectedCodeValue.a_code.key !== 'X') {
            this.componentData.selectedCodeValue.b_code.first.key = 'Y';
            this.componentData.selectedCodeVAlue.b_code.second.key = 'Z';
        }
    }
}
</script>
```
