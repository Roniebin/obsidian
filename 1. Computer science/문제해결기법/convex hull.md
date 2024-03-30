``` java 
import java.io.BufferedReader;

import java.io.BufferedWriter;

import java.io.FileReader;

import java.io.FileWriter;

import java.util.ArrayList;

import java.util.Collections;

import java.util.Comparator;

import java.util.Stack;

import java.util.StringTokenizer;

import java.util.stream.Stream;

  

class Point {

    int x = 0;

    int y = 0;

    double angle = 0;

    double distance = 0;

  

    Point(int x, int y, double angle, double distance) {

        this.x = x;

        this.y = y;

        this.angle = angle;

        this.distance = distance;

    }

}

  

public class hull {

  

    public static int ccw2(int a, int b, int c, int d) {

        return (a * d) - (b * c);

    }

  

    public static int ccw(Point r, Point p, Point q) {

        return ccw2(p.x - r.x, p.y - r.y, q.x - r.x, q.y - r.y);

    }

  

    public static double CalcAngle(Point r, Point p) {

        double angle = Math.toDegrees(Math.atan2(p.y - r.y, p.x - r.x));

  

        return angle;

    }

  

    public static double CalcDistance(Point r, Point p) {

        double distance = Math.sqrt(Math.pow(r.x - p.x, 2) + Math.pow(r.y - p.y, 2));

        return distance;

    }

  

    public static void main(String agrs[]) throws Exception {

  

        try {

            FileReader fileReader = new FileReader("hull.inp");

            BufferedReader br = new BufferedReader(fileReader);

            FileWriter fileWriter = new FileWriter("hull.out");

            BufferedWriter bw = new BufferedWriter(fileWriter);

  

            StringBuilder sb = new StringBuilder();

  

            int n = Integer.parseInt(br.readLine());

  

            ArrayList<Point> result = new ArrayList<>();

  

            int min_y = 1000000;

            int min_x = 1000000;

            int min_idx = -1;

            Point center_point = new Point(0, 0, 0, 0);

  

            for (int i = 0; i < n; i++) {

                StringTokenizer st = new StringTokenizer(br.readLine());

                int x = Integer.parseInt(st.nextToken());

                int y = Integer.parseInt(st.nextToken());

  

                // 기준점 잡기---------------------------------------

                Point point = new Point(x, y, 0, 0);

  

                if (min_x > x) {

                    center_point = point;

                    min_x = x;

                    min_idx = i;

                    min_y = y;

                } else if (min_x == x) {

                    if (min_y > y) {

                        center_point = point;

                        min_y = y;

                        min_idx = i;

                    }

                }

                result.add(point);

            }

  

            Point temp = result.get(0);

            result.set(0, center_point);

            result.set(min_idx, temp);

  

            // 기준점 잡기 완료 ----------------------------------------

  

            for (int i = 0; i < n; i++) {

                result.get(i).angle = CalcAngle(result.get(0), result.get(i));

                result.get(i).distance = CalcDistance(result.get(0), result.get(i));

            }

  

            Point t = result.get(0);

            result.remove(0);

            // 각 기준으로 오름차순 각이같으면 기준점과의 거리가 큰걸 먼저

            Collections.sort(result, (p1, p2) -> {

                if (p1.angle < p2.angle)

                    return -1;

                else if (p1.angle > p2.angle)

                    return 1;

                else {

                    double distance1 = p1.distance;

                    double distance2 = p2.distance;

                    return Double.compare(distance2, distance1);

                }

            });

  

            result.add(0, t);

  

            ArrayList<Point> bucket = new ArrayList<>();

  

            bucket.add(result.get(0));

            bucket.add(result.get(1));

  

            int link = 2;

            int present = link;

  

            while (link != result.size()) {

                int checker = ccw(bucket.get(present - 2), bucket.get(present - 1), result.get(link));

                // checker 가 양수이면 좌회전 ,좌회전은 스택에넣는다

                if (checker > 0) {

                    bucket.add(result.get(link));

                    present += 1;

                    link += 1;

                } else if (checker < 0) {

                    present -= 1;

                    bucket.remove(present);

                } else {

  

                }

  

            }

  

            int checker2 = ccw(bucket.get(present - 2), bucket.get(present - 1), result.get(0));

  

            if (checker2 <= 0) {

                bucket.remove(present - 1);

            }

  

            sb.append(bucket.size() + "\n");

            for (int i = 0; i < bucket.size(); i++) {

                sb.append(bucket.get(i).x + " " + bucket.get(i).y + "\n");

            }

  

            bw.write(sb.toString().trim());

            bw.flush();

  

        } catch (Exception e) {

  

        }

    }

}
```