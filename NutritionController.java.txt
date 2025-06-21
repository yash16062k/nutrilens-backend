package com.nutrilens.nutrilens_backend.controller;

import com.nutrilens.nutrilens_backend.service.NutritionService;
import org.springframework.web.bind.annotation.*;

import java.util.*;

@RestController
@RequestMapping("/api/nutrition")
public class NutritionController {

    private final NutritionService nutritionService;

    public NutritionController(NutritionService nutritionService) {
        this.nutritionService = nutritionService;
    }

    @PostMapping("/lookup")
    public Map<String, Object> getNutrition(@RequestBody Map<String, String> request) {
        String item = request.get("item");
        return nutritionService.lookup(item);
    }
}
