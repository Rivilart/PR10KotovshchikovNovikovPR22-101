# PR10KotovshchikovNovikovPR22-101
package com.example.a10kotovshchikovnovikovpr22_101;

import android.content.Context;
import android.content.res.Resources;
import android.graphics.Bitmap;
import android.graphics.BitmapFactory;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.Rect;
import android.view.View;

public class Draw2D extends View {

    private Paint mPaint = new Paint();
    private Bitmap mBitmap;


    public Draw2D(Context context) {

        super(context);
        Resources res = this.getResources();
        mBitmap = BitmapFactory.decodeResource(res, R.mipmap.cat_foreground);

    }
    private Rect mRect = new Rect();

    @Override

    protected void onDraw(Canvas canvas){

        super.onDraw(canvas);
        float width = getWidth();
        float height = getHeight();
        mPaint.setStyle(Paint.Style.FILL);
        mPaint.setColor(Color.WHITE);
        canvas.drawPaint(mPaint);
        mPaint.setAntiAlias(true);
        mPaint.setColor(Color.YELLOW);
        canvas.drawCircle(950, 30, 25, mPaint);
        mPaint.setColor(Color.GREEN);
        canvas.drawRect(0, canvas.getHeight() - 30, width, height, mPaint);
        mPaint.setColor(Color.BLUE);
        mPaint.setStyle(Paint.Style.FILL);
        mPaint.setAntiAlias(true);
        mPaint.setTextSize(32);
        canvas.drawText("Лужайка только для котов", 30, height - 32, mPaint);
        int x = 810;
        int y = 190;
        mPaint.setColor(Color.GRAY);
        mPaint.setTextSize(27);
        String str2rotate = "Лучиксолнца!";
        canvas.save();
        canvas.rotate(-45, x + mRect.exactCenterX(), y + mRect.exactCenterY());
        mPaint.setStyle(Paint.Style.FILL);
        canvas.drawText(str2rotate, x, y, mPaint);
        canvas.restore();

        canvas.drawBitmap(mBitmap, width - mBitmap.getWidth(), height - mBitmap.getHeight() - 10, mPaint);

    }
}

package com.example.a10kotovshchikovnovikovpr22_101;

import android.os.Bundle;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        Draw2D draw2D = new Draw2D(this);
        setContentView(draw2D);



    }
}
