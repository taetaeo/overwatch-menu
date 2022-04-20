# SCSS 리팩토링

## scss 사용방법

- 터미널에서 `npm` 설치

```sh
npm init -y
npm i -D parcel-bundler
```

- `package.json` 파일에 들어가서, `script` 부분에 다음과 같이 작성
  -   `"dev": "parcel index.html",`
  -   `"build": "parcel build index.html"`

- `index.html` 파일에서  scss 파일 연결

```html
 <link rel="stylesheet" href="./main.scss"/>
```

<br/>

## 변경된 SCSS

```scss
$url: "https://raw.githubusercontent.com/ohtaekwon/overwatch-menu/master/images";

body {
  height: 100vh;
  background-image: url("#{$url}/bg.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
.container {
  padding: 50px 0;
  .heroes {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 660px;
    margin: 0 auto;
    padding: 40px 20px;
    .hero {
      width: 80px;
      height: 84px;
      margin: 4px;
      border: 3px solid #fff;
      border-radius: 10px;
      box-sizing: border-box;
      overflow: hidden;
      background-color: #555;
      transform: skewX(-14deg);
      transition:
              transform .1s,
              background-color .6s;
      &:hover {
        background-color: #ff9c00;
        transform: skewX(-14deg) scale(1.3);
        z-index: 1;
      }
      .image {
        width: 140%;
        height: 100%;
        transform: translateX(-16px) skewX(14deg);
        background-position: center;
        background-repeat: no-repeat;
        background-size: 90px;
      }
      @for $i from 1 through 32 {
        // .hero
        &:nth-child(#{$i}) .image {
          background-image: url("#{$url}/hero#{$i}.png");
        }
      }
    }
  }
  .logo {
    max-width: 300px;
    margin: 0 auto;
    padding: 0 20px;
    img {
      width: 100%;
    }
  }
}


```