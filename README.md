# bar-project
이수 시스템 인턴을 진행하며 맡은 프로젝트중 일부이며, Google에서 제공하는 google charts의 timeline chart를 활용하여 차트가 보이도록 하였습니다. 

![43123](https://user-images.githubusercontent.com/52379503/128815595-496fa0e1-da6d-4d7e-a5f9-c6d33fd15ae7.png)

위와 같이 타임라인이 보이도록 하였고 startDay, endDay를 각 item마다 가지고 있으며 그 값을 전달하게 되면 해당 Day값에 맞도록 타임라인 바를 형성해줍니다. 그리고 item이 가지고있는 title이라는 파라메터에 따라 item의 y축 위치가 결정되게 됩니다. timeline이 점점 지날때 마다 색이 옅어지도록 프로그래밍 하였으며 각 가로축 라인별로 통일된 색을 가지도록 했습니다. 이 프로젝트 또한 Json 데이터를 받아 해당 데이터를 토대로 타임라인이 보이도록 구성했습니다.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
