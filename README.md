# 21552011144_Azki Maulana Assariy_UTS_WEB2
# Langkah-Langkah Membuat Migrasi dan Model pada Laravel

## 1. Buat Migrasi untuk Tabel:

Jalankan perintah berikut di terminal Laravel untuk membuat migrasi:

```bash
php artisan make:migration create_hewan_table --create=hewan
```
Edit file migrasi yang dibuat (`database/migrations/timestamp_create_hewan_table.php`) untuk menentukan struktur tabel hewan. Contoh:

```php
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateHewanTable extends Migration
{
    public function up()
    {
        Schema::create('hewan', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->string('jenis');
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('hewan');
    }
}
```
Jalankan migrasi dengan perintah:
```bash
php artisan migrate
```
## 2. Buat Model:
Edit file model yang dibuat (`app/Models/Hewan.php`) untuk menyesuaikan dengan struktur tabel:
```php
namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Hewan extends Model
{
    use HasFactory;

    protected $table = 'hewan';
    protected $fillable = ['nama', 'jenis'];
}
```

