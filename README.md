# processing_templates

TODO: ボール動かすゲームです。

## Usage

TODO: 矢印が動く物体に当たらないように、ボールをゴール地点まで持って行きます。
付いてくるボールに当たってもいけません。2回当たるとgame overです。

## Code review

TODO:void setup() {
  size(1200, 600);
  strokeWeight(2);
  textSize(50);
  textAlign(CENTER);
}

float mx;
float my;
float easing = 0.02;
int radius =30;
int inner= radius;
int count=0;
boolean flag = false;
float x=radius;
float y=radius;
float z=radius;
float speed1=12;
float speed2=15;
float speed3=10;
void draw() { 

  background(223);
  x+=speed1;
  if (x>width-radius) {
    x=-radius;
  }
  fill (250, 0, 0);//red
  rect(x-600, 90, 200, 50);
  rect(x, 90, 200, 50);
  rect(600+x, 90, 200, 50);

  y+=speed2;
  if (y>width+radius) {
    y=radius;
  }

  fill(0, 255, 0); //green
  rect(800-y, 200, 500, 20);

  z+=speed3;
  if (z>width+radius) {
    z=radius;
  }


  fill(255, 255, 0);//yellow
  rect(-1000+z, 300, 20, 100);
  rect(-800+z, 300, 20, 100);
  rect(-600+z, 300, 20, 100);
  rect(-400+z, 300, 20, 100);
  rect(-200+z, 300, 20, 100);
  rect(z, 300, 20, 100);
  rect(200+z, 300, 20, 100);
  rect(400+z, 300, 20, 100);
  rect(600+z, 300, 20, 100);
  rect(800+z, 300, 20, 100);
  rect(1000+z, 300, 20, 100);
  rect(1200+z, 300, 20, 100);


  if (abs(mouseX - mx) > 0.1) {
    mx = mx + (mouseX - mx) * easing;
  }
  if (abs(mouseY - my) > 0.1) {
    my = my + (mouseY- my) * easing;
  }
  mx = constrain(mx, inner, width - inner);
  my = constrain(my, inner, height - inner);
  fill(255, 255, 255);
  ellipse(mx, my, radius, radius);

  text("start", 600, 40);
  text("goal", 600, 580);
 
  if (my<60) {

    text("avoid the objects and reach the goal", 600, 300);
  }

  if (my>540) {

    fill(184, 98, 99);
    text("finish", 600, 300);
    noLoop();
  }
  color c = get(mouseX, mouseY); 
  if (c != -2105377 && c != -16777216 && flag == false) 
  {
    count++; 
    flag = true;
    fill(0);
     text("Miss", mx+20,my+20, 300);
  }
  if (c == -2105377 && flag == true) 
  {
    flag = false;
  }
  text(count, 50, 560);
  
if(count>1)
{
  textSize(100);
  fill(255,0,0);
  text("GameOver",600,300);
  noLoop();
}
}

ゲームを作ってみたくて一番シンプルそうなものを考えました。

引用
Constrain.  https://processing.org/examples/constrain.html

## License

ここではサンプルとしてMITライセンスの表示をしています．Creative commonsとかLGPLでもOKです．
[Githubのライセンシングを解説した記事](https://www.catch.jp/oss-license/2013/09/10/github/)は
とても参考になります(だいぶその時...2013か...からは改訂されてるけど)．

The processing application is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Test project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/[USERNAME]/processing_templates/blob/master/CODE_OF_CONDUCT.md).
